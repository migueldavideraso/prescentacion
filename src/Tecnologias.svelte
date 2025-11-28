<script>
  // Datos de las tecnologías
  const categorias = [
    {
      titulo: "Frameworks para Agentes y Orquestación",
      tecnologias: [
        {
          nombre: "CrewAI",
          descripcion: "Permite crear \"equipos\" de agentes con roles, objetivos y comunicación entre ellos. Útil para sistemas colaborativos o pipelines complejos."
        },
        {
          nombre: "LangChain / LangGraph",
          descripcion: "Estructuras para construir agentes avanzados, cadenas de razonamiento, RAG, flujos de decisión y máquinas de estados. Muy útil para agentes conversacionales y flujos que requieren memoria o pasos definidos."
        }
      ]
    },
    {
      titulo: "Bases de Datos",
      tecnologias: [
        {
          nombre: "Turso",
          descripcion: "Base de datos SQL distribuida y extremadamente rápida. Basada en libSQL, bifurcación de SQLite, optimizada para edge computing y aplicaciones globales. Ofrece baja latencia, alta disponibilidad y sincronización de datos en tiempo real."
        },
        {
          nombre: "Supabase",
          descripcion: "Alternativa open source a Firebase con Postgres, autenticación, almacenamiento y funciones edge. Ideal para proyectos que requieren una base de datos relacional completa con API REST y tiempo real."
        },
        {
          nombre: "PlanetScale",
          descripcion: "Base de datos MySQL serverless, escalable y distribuida globalmente. Ofrece ramificaciones de bases de datos (similar a git) y despliegue sin tiempo de inactividad."
        }
      ],
      nota: "Todas ofrecen planes gratuitos con límites generosos, perfectos para desarrollo y proyectos iniciales."
    },
    {
      titulo: "Scraping y Obtención de Datos Públicos",
      tecnologias: [
        {
          nombre: "Apify",
          descripcion: "Plataforma para crear scrapers y \"actors\" capaces de extraer datos públicos a escala (productos, precios, listados, perfiles, reseñas)."
        },
        {
          nombre: "Serper.dev",
          descripcion: "API de búsqueda parecida a Google Search. Facilita que los agentes recuperen información actualizada desde la web."
        }
      ]
    },
    {
      titulo: "Automatización y Workflows (no-code / low-code)",
      tecnologias: [
        {
          nombre: "n8n",
          descripcion: "Herramienta open-source para construir flujos complejos con nodos, APIs, scraping, agentes y procesos automatizados."
        },
        {
          nombre: "Make (Integromat)",
          descripcion: "Orquestación visual para conectar servicios, agentes, bases de datos y pasos de IA en una misma línea de trabajo."
        },
        {
          nombre: "Zapier",
          descripcion: "Automatizador simple para conectar formularios, APIs, documentos, alertas y activar pasos del agente."
        }
      ],
      regla: "Los flujos deben ser creados por el equipo. No se permiten plantillas listas sin modificaciones profundas."
    },
    {
      titulo: "Notas, Datos Internos y Mini-Bases",
      tecnologias: [
        {
          nombre: "Notion",
          descripcion: "Base de datos simple + documentación + contenido estructurado."
        }
      ],
      usos: [
        "Almacenar FAQs, inventarios, propiedades, vacantes",
        "Crear bases tipo CRM",
        "Alimentar agentes con contexto organizado",
        "Documentar el diseño del proyecto"
      ],
      nota: "Perfecta para equipos que no quieren montar un backend complejo desde cero."
    }
  ];
</script>

<div class="container">
  <h1>Tecnologías para Agentes y Automatización</h1>
  <p class="subtitle">Todas con plan gratuito disponible</p>
  
  <div class="tech-container">
    {#each categorias as categoria, i}
      <div class="tech-card">
        <h2>{i + 1}) {categoria.titulo}</h2>
        <div class="tech-list">
          {#each categoria.tecnologias as tech}
            <div class="tech-item">
              <h3>{tech.nombre}</h3>
              <p>{@html tech.descripcion}</p>
            </div>
          {/each}
        </div>
        
        {#if categoria.regla}
          <div class="tech-rule">
            <h4>📌 Regla:</h4>
            <p>{categoria.regla}</p>
          </div>
        {/if}
        
        {#if categoria.usos}
          <div class="tech-uses">
            <h4>Se puede usar para:</h4>
            <ul>
              {#each categoria.usos as uso}
                <li>{uso}</li>
              {/each}
            </ul>
          </div>
        {/if}
        
        {#if categoria.nota}
          <div class="tech-note">
            <p>{categoria.nota}</p>
          </div>
        {/if}
      </div>
    {/each}
  </div>
  
  <div class="back-link">
    <a href="#/" class="btn-volver">Volver a Enlaces QR</a>
  </div>
</div>

<style>
  .subtitle {
    text-align: center;
    margin-top: -0.5rem;
    margin-bottom: 2rem;
    color: #94a3b8;
    font-size: 1.1rem;
  }
  
  .tech-container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1.5rem;
    margin-bottom: 2rem;
  }
  
  .tech-card {
    background-color: rgba(30, 41, 59, 0.6);
    backdrop-filter: blur(10px);
    border-radius: 16px;
    padding: 1.5rem;
    border: 1px solid rgba(255, 255, 255, 0.1);
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  }
  
  .tech-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.2), 0 10px 10px -5px rgba(0, 0, 0, 0.1);
    border-color: rgba(255, 255, 255, 0.2);
  }
  
  .tech-card h2 {
    font-size: 1.5rem;
    margin-top: 0;
    margin-bottom: 1rem;
    color: #f1f5f9;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    padding-bottom: 0.75rem;
    background: linear-gradient(90deg, #3b82f6, #6366f1);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  
  .tech-item {
    margin-bottom: 1rem;
    padding-bottom: 1rem;
    border-bottom: 1px dashed rgba(255, 255, 255, 0.1);
  }
  
  .tech-item:last-child {
    border-bottom: none;
    padding-bottom: 0;
  }
  
  .tech-item h3 {
    font-size: 1.2rem;
    margin: 0.5rem 0;
    color: #f8fafc;
  }
  
  .tech-item p {
    font-size: 0.9rem;
    color: #cbd5e1;
    line-height: 1.5;
    margin: 0.5rem 0;
  }
  
  .tech-rule, .tech-note {
    margin-top: 1rem;
    padding: 1rem;
    background-color: rgba(99, 102, 241, 0.1);
    border-radius: 8px;
    border-left: 3px solid #6366f1;
  }
  
  .tech-rule h4, .tech-uses h4 {
    margin: 0 0 0.5rem 0;
    color: #e2e8f0;
    font-size: 1rem;
  }
  
  .tech-uses {
    margin-top: 1rem;
  }
  
  .tech-uses ul {
    margin: 0.5rem 0;
    padding-left: 1.5rem;
    color: #cbd5e1;
  }
  
  .tech-uses li {
    margin-bottom: 0.5rem;
    font-size: 0.9rem;
  }
  
  .back-link {
    text-align: center;
    margin: 2rem 0;
  }
  
  .btn-volver {
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
  
  .btn-volver:hover {
    transform: scale(1.05);
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
  }
  
  @media (max-width: 1100px) {
    .tech-container {
      grid-template-columns: 1fr;
    }
  }
</style>
