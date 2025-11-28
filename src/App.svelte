<script>
  import { onMount } from 'svelte';
  import QRCode from 'qrcode';
  import Tecnologias from './Tecnologias.svelte';
  
  // Estado para manejar la navegación entre páginas
  let currentPage = 'qr'; // 'qr' o 'tech'
  
  // Función para cambiar de página
  function navigateTo(page) {
    currentPage = page;
  }

  const enlaces = [
    { url: 'https://lovable.dev/', nombre: 'Lovable.dev' },
    { url: 'https://v0.app/', nombre: 'v0.app' },
    { url: 'https://www.claude.com/product/claude-code', nombre: 'Claude Code' },
    { url: 'https://codeassist.google/', nombre: 'Google Code Assist' },
    { url: 'https://windsurf.com/editor', nombre: 'Windsurf Editor' },
    { url: 'https://antigravity.google/', nombre: 'Google Antigravity' },
    { url: 'https://www.trae.ai/', nombre: 'Trae AI' }
  ];

  onMount(() => {
    // Manejar navegación con hash
    const handleHashChange = () => {
      const hash = window.location.hash;
      if (hash === '#/tech') {
        currentPage = 'tech';
      } else {
        currentPage = 'qr';
      }
    };
    
    // Inicializar según el hash actual
    handleHashChange();
    
    // Escuchar cambios en el hash
    window.addEventListener('hashchange', handleHashChange);
    
    // Renderizar códigos QR si estamos en la página de QR
    if (currentPage === 'qr') {
      enlaces.forEach((enlace, i) => {
        const canvas = document.getElementById(`qr-${i}`);
        if (canvas) {
          QRCode.toCanvas(canvas, enlace.url, { width: 120, margin: 0, color: { dark: "#000000", light: "#ffffff" } }, function (error) {
            if (error) console.error(error);
          });
        }
      });
    }
    
    // Cleanup al desmontar
    return () => {
      window.removeEventListener('hashchange', handleHashChange);
    };
  });
</script>

<div class="nav-container">
  <nav>
    <a href="#/" class={currentPage === 'qr' ? 'active' : ''}>Enlaces QR</a>
    <a href="#/tech" class={currentPage === 'tech' ? 'active' : ''}>Tecnologías</a>
  </nav>
</div>

{#if currentPage === 'qr'}
  <div class="container">
    <h1>Enlaces con Códigos QR</h1>
    
    <div class="enlaces-grid">
      {#each enlaces as enlace, i}
        <div class="enlace-card">
          <div class="enlace-content">
            <div class="qr-code">
              <canvas id="qr-{i}"></canvas>
            </div>
            <h3>{enlace.nombre}</h3>
            <a href={enlace.url} target="_blank" rel="noopener noreferrer" class="enlace-url">
              {enlace.url}
            </a>
            <a href={enlace.url} target="_blank" rel="noopener noreferrer" class="btn-visitar">Visitar</a>
          </div>
        </div>
      {/each}
    </div>
    
    <div class="page-actions">
      <a href="#/tech" class="btn-nav">Ver Tecnologías →</a>
    </div>
  </div>
{:else}
  <Tecnologias />
{/if}

<style>
  .nav-container {
    width: 100%;
    display: flex;
    justify-content: center;
    padding: 1rem 0;
    position: sticky;
    top: 0;
    z-index: 100;
    background: rgba(15, 23, 42, 0.8);
    backdrop-filter: blur(10px);
  }
  
  nav {
    display: flex;
    gap: 1rem;
    padding: 0.5rem 1rem;
    border-radius: 9999px;
    background: rgba(30, 41, 59, 0.6);
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
    border: 1px solid rgba(255, 255, 255, 0.1);
  }
  
  nav a {
    padding: 0.5rem 1.25rem;
    border-radius: 9999px;
    text-decoration: none;
    color: #cbd5e1;
    font-weight: 500;
    transition: all 0.3s ease;
  }
  
  nav a.active {
    background: linear-gradient(90deg, #3b82f6, #6366f1);
    color: white;
    box-shadow: 0 4px 6px -1px rgba(59, 130, 246, 0.3);
  }
  
  nav a:hover:not(.active) {
    color: white;
    background: rgba(99, 102, 241, 0.1);
  }
  
  .page-actions {
    margin-top: 2rem;
    text-align: center;
  }
  
  .btn-nav {
    display: inline-block;
    background: linear-gradient(90deg, #6366f1, #3b82f6);
    color: white;
    text-decoration: none;
    padding: 0.75rem 1.5rem;
    border-radius: 9999px;
    font-size: 1rem;
    font-weight: 500;
    transition: all 0.3s ease;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
  }
  
  .btn-nav:hover {
    transform: scale(1.05);
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
  }
</style>