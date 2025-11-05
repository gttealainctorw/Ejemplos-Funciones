<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Ejemplos-Funciones — Fundamentos de programación</title>
  <style>
    :root{
      --bg:#f0f2f5; --card:#ffffff; --muted:#657786; --accent:#1877f2; --accent-2:#0b66c3; --glass: rgba(3,6,12,0.04);
      --radius:12px; --shadow: 0 6px 18px rgba(3,12,28,0.08);
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    }
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;background:linear-gradient(180deg,var(--bg),#e9eef7);color:#0f1724}

    /* Topbar (Facebook-like) */
    .topbar{position:sticky;top:0;z-index:60;background:rgba(255,255,255,0.96);backdrop-filter:blur(6px);border-bottom:1px solid rgba(16,24,40,0.04)}
    .topbar .inner{max-width:1100px;margin:0 auto;display:flex;align-items:center;gap:16px;padding:10px 16px}
    .brand{display:flex;align-items:center;gap:12px}
    .logo{width:42px;height:42px;border-radius:10px;background:linear-gradient(135deg,var(--accent),var(--accent-2));display:flex;align-items:center;justify-content:center;color:white;font-weight:700}
    .title{font-weight:700;font-size:16px}

    .search{flex:1;display:flex;justify-content:center}
    .search input{width:60%;min-width:220px;padding:10px 12px;border-radius:999px;border:1px solid rgba(15,23,36,0.06);box-shadow:var(--shadow);outline:none}

    .actions{display:flex;gap:12px;align-items:center}
    .btn{background:transparent;border:0;padding:8px 12px;border-radius:8px;cursor:pointer;font-weight:600}
    .btn.primary{background:var(--accent);color:white}

    /* Layout */
    .layout{max-width:1100px;margin:28px auto;display:grid;grid-template-columns:260px 1fr 320px;gap:20px;padding:0 16px}

    /* Left sidebar */
    .sidebar{background:var(--card);border-radius:var(--radius);box-shadow:var(--shadow);padding:14px;border:1px solid rgba(15,23,36,0.04)}
    .menu{list-style:none;padding:0;margin:0}
    .menu li{padding:10px;border-radius:8px;display:flex;align-items:center;gap:10px;color:var(--muted);cursor:pointer}
    .menu li:hover{background:var(--glass);color:var(--accent)}

    /* Main card */
    .card{background:var(--card);border-radius:var(--radius);padding:18px;box-shadow:var(--shadow);border:1px solid rgba(15,23,36,0.04)}
    h1{margin:0;font-size:20px;color:#111827}
    p.lead{color:var(--muted);margin-top:8px}

    /* Topics list */
    .topics{display:grid;grid-template-columns:repeat(2,1fr);gap:12px;margin-top:16px}
    .topic{padding:12px;border-radius:10px;border:1px solid rgba(3,12,28,0.04);background:linear-gradient(180deg, #fff, #fbfdff);display:flex;align-items:center;justify-content:space-between}
    .topic .left{display:flex;flex-direction:column}
    .topic h3{margin:0;font-size:14px}
    .topic p{margin:6px 0 0;color:var(--muted);font-size:13px}

    /* Right panel */
    .panel{position:sticky;top:80px}
    .meta{font-size:13px;color:var(--muted)}

    /* Footer */
    footer{text-align:center;margin:36px 0;color:var(--muted)}

    /* Responsive */
    @media (max-width:1000px){.layout{grid-template-columns:1fr;}.search input{width:100%}.topics{grid-template-columns:1fr}}

    /* subtle micro-interactions */
    .pulse{position:relative}
    .pulse::after{content:'';position:absolute;right:8px;top:50%;transform:translateY(-50%);width:8px;height:8px;border-radius:50%;background:var(--accent);box-shadow:0 0 8px rgba(24,119,242,0.45)}
  </style>
</head>
<body>
  <div class="topbar">
    <div class="inner">
      <div class="brand">
        <div class="logo">EF</div>
        <div>
          <div class="title">Ejemplos-Funciones</div>
          <div style="font-size:12px;color:var(--muted)">Equipo 1 — Fundamentos de programación</div>
        </div>
      </div>

      <div class="search">
        <input id="searchInput" placeholder="Buscar tema (ej.: recursiva, alcance)..." />
      </div>

      <div class="actions">
        <button class="btn" id="toggleView">Alternar vista</button>
        <button class="btn primary" id="copyLink">Copiar link</button>
      </div>
    </div>
  </div>

  <main class="layout">
    <aside class="sidebar card">
      <div style="font-weight:700;margin-bottom:8px">Navegación</div>
      <ul class="menu">
        <li data-target="definicion">Definición y estructura</li>
        <li data-target="parametros">Parámetros y argumentos</li>
        <li data-target="retorno">Funciones con retorno</li>
        <li data-target="procedimientos">Procedimientos (sin retorno)</li>
        <li data-target="alcance">Alcance de variables</li>
        <li data-target="flujo">Llamadas y flujo</li>
        <li data-target="recursivas">Funciones recursivas</li>
        <li data-target="practicas">Buenas prácticas</li>
      </ul>
    </aside>

    <section class="card" id="main">
      <h1>Temas de la exposición</h1>
      <p class="lead">Aquí se listan los temas que se cubrirán durante la presentación. Usa el buscador o la navegación lateral para filtrar.</p>

      <div class="topics" id="topicsList">
        <div class="topic" data-keywords="definicion estructura firma retorno">
          <div class="left">
            <h3>Definición y estructura de una función</h3>
            <p>Elementos: nombre, parámetros, tipo de retorno, cuerpo.</p>
          </div>
          <div>+</div>
        </div>

        <div class="topic" data-keywords="parametros argumentos paso valor referencia">
          <div class="left">
            <h3>Parámetros y argumentos</h3>
            <p>Diferencia entre parámetro y argumento; paso por valor vs referencia.</p>
          </div>
          <div>+</div>
        </div>

        <div class="topic" data-keywords="retorno valor tipo funciones retorno">
          <div class="left">
            <h3>Funciones con retorno</h3>
            <p>Cómo regresar valores y usar el resultado.</p>
          </div>
          <div>+</div>
        </div>

        <div class="topic" data-keywords="procedimiento void sin retorno">
          <div class="left">
            <h3>Procedimientos (sin retorno)</h3>
            <p>Acciones que modifican estado o imprimen resultados.</p>
          </div>
          <div>+</div>
        </div>

        <div class="topic" data-keywords="alcance scope local global variables">
          <div class="left">
            <h3>Alcance de variables (scope)</h3>
            <p>Locales, globales, y shadowing.</p>
          </div>
          <div>+</div>
        </div>

        <div class="topic" data-keywords="llamadas flujo main orden ejecucion">
          <div class="left">
            <h3>Llamadas y flujo de ejecución</h3>
            <p>Orden de ejecución y paso entre funciones.</p>
          </div>
          <div>+</div>
        </div>

        <div class="topic" data-keywords="recursiva factorial ejemplo stack overflow">
          <div class="left">
            <h3>Funciones recursivas</h3>
            <p>Concepto, casos base y profundidad de pila.</p>
          </div>
          <div>+</div>
        </div>

        <div class="topic" data-keywords="modularidad buenas practicas nombres comentarios">
          <div class="left">
            <h3>Buenas prácticas de diseño modular</h3>
            <p>Nombres descriptivos, documentación y separación de responsabilidades.</p>
          </div>
          <div>+</div>
        </div>

      </div>
    </section>

    <aside class="card panel">
      <div style="display:flex;justify-content:space-between;align-items:center">
        <div>
          <div style="font-weight:700">Detalles</div>
          <div class="meta">Lenguaje: C — Formato: HTML para presentación</div>
        </div>
        <div style="text-align:right">
          <div style="font-weight:700;color:var(--accent)">Equipo 1</div>
          <div style="font-size:12px;color:var(--muted)">Fecha: (añade la fecha de tu presentación)</div>
        </div>
      </div>

      <hr style="margin:14px 0;border:none;border-top:1px solid rgba(15,23,36,0.04)" />

      <div style="font-weight:700;margin-bottom:8px">Acciones</div>
      <div style="display:flex;gap:8px">
        <button class="btn" id="downloadJson">Descargar temas (.json)</button>
        <button class="btn" id="print">Imprimir</button>
      </div>

      <div style="margin-top:14px;font-size:13px;color:var(--muted)">Personaliza colores o añade un logo desde el archivo HTML si lo deseas.</div>
    </aside>
  </main>

  <footer>
    Hecho con ❤️ por <strong>Equipo 1</strong> — Fundamentos de programación
  </footer>

  <script>
    // Interactividad simple: búsqueda, navegación y utilidades
    const searchInput = document.getElementById('searchInput');
    const topics = Array.from(document.querySelectorAll('.topic'));
    const menuItems = Array.from(document.querySelectorAll('.menu li'));

    function filterTopics(q){
      const ql = q.trim().toLowerCase();
      topics.forEach(t => {
        const keys = t.dataset.keywords || '';
        t.style.display = keys.toLowerCase().includes(ql) || ql === '' ? 'flex' : 'none';
      })
    }

    searchInput.addEventListener('input', e => filterTopics(e.target.value));

    // Smooth scroll to topic when clicking left menu
    menuItems.forEach(mi => mi.addEventListener('click', () => {
      const target = document.querySelector(`[data-keywords*="${mi.dataset.target}"]`);
      if(target) target.scrollIntoView({behavior:'smooth', block:'center'});
    }));

    // Copy link placeholder (copies current page URL)
    document.getElementById('copyLink').addEventListener('click', async () => {
      try{
        await navigator.clipboard.writeText(location.href);
        alert('Enlace copiado al portapapeles.');
      }catch(e){
        alert('No se pudo copiar.');
      }
    });

    // Toggle compact view (mimic 'alternar vista')
    const layout = document.querySelector('.layout');
    document.getElementById('toggleView').addEventListener('click', () => {
      layout.classList.toggle('compact');
      if(layout.classList.contains('compact')){
        layout.style.gridTemplateColumns = '1fr';
      }else{
        layout.style.gridTemplateColumns = '260px 1fr 320px';
      }
    });

    // Download topics as JSON
    document.getElementById('downloadJson').addEventListener('click', () => {
      const data = topics.map(t => ({title: t.querySelector('h3').innerText, description: t.querySelector('p').innerText, keywords: t.dataset.keywords}));
      const blob = new Blob([JSON.stringify(data, null, 2)], {type:'application/json'});
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a'); a.href = url; a.download = 'temas-funciones.json'; a.click(); URL.revokeObjectURL(url);
    });

    // Print action
    document.getElementById('print').addEventListener('click', () => window.print());
  </script>
</body>
</html>
