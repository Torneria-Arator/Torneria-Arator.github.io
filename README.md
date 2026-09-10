<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tornería Arator</title>
<link href="https://fonts.googleapis.com/css2?family=Rajdhani:wght@400;500;600;700&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --negro: #0D1117;
    --oscuro: #1C2128;
    --medio: #2D333B;
    --plata: #8B9099;
    --plata-clara: #C9CDD3;
    --naranja: #1A6FE8;
    --naranja-suave: #4A8FF0;
    --blanco: #F0F2F5;
  }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Inter', sans-serif;
    background: var(--negro);
    color: var(--blanco);
    line-height: 1.6;
  }

  /* NAV */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.2rem 4rem;
    background: rgba(13, 17, 23, 0.92);
    backdrop-filter: blur(8px);
    border-bottom: 1px solid rgba(139, 144, 153, 0.15);
  }

  .logo {
    font-family: 'Rajdhani', sans-serif;
    font-size: 1.5rem;
    font-weight: 700;
    letter-spacing: 0.05em;
    color: var(--blanco);
  }

  .logo span { color: var(--naranja); }

  nav ul {
    list-style: none;
    display: flex;
    gap: 2.5rem;
  }

  nav ul a {
    text-decoration: none;
    color: var(--plata);
    font-size: 0.875rem;
    font-weight: 500;
    letter-spacing: 0.02em;
    transition: color 0.2s;
  }

  nav ul a:hover { color: var(--blanco); }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    padding: 8rem 4rem 4rem;
    position: relative;
    overflow: hidden;
    background: var(--negro);
  }

  .hero::before {
    content: '';
    position: absolute;
    inset: 0;
    background:
      repeating-linear-gradient(
        90deg,
        rgba(139,144,153,0.03) 0px,
        rgba(139,144,153,0.03) 1px,
        transparent 1px,
        transparent 60px
      ),
      repeating-linear-gradient(
        0deg,
        rgba(139,144,153,0.03) 0px,
        rgba(139,144,153,0.03) 1px,
        transparent 1px,
        transparent 60px
      );
  }

  .hero::after {
    content: '';
    position: absolute;
    right: -10%;
    top: 50%;
    transform: translateY(-50%);
    width: 600px;
    height: 600px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(26,111,232,0.12) 0%, transparent 70%);
    pointer-events: none;
  }

  .hero-content {
    position: relative;
    z-index: 1;
    max-width: 700px;
  }

  .hero-eyebrow {
    font-family: 'Rajdhani', sans-serif;
    font-size: 0.875rem;
    font-weight: 600;
    color: var(--naranja);
    letter-spacing: 0.15em;
    margin-bottom: 1.5rem;
    display: flex;
    align-items: center;
    gap: 0.75rem;
  }

  .hero-eyebrow::before {
    content: '';
    display: inline-block;
    width: 2rem;
    height: 2px;
    background: var(--naranja);
  }

  .hero h1 {
    font-family: 'Rajdhani', sans-serif;
    font-size: clamp(3rem, 7vw, 5.5rem);
    font-weight: 700;
    line-height: 1.05;
    color: var(--blanco);
    margin-bottom: 1.5rem;
  }

  .hero h1 em {
    font-style: normal;
    color: var(--naranja);
  }

  .hero p {
    font-size: 1.125rem;
    color: var(--plata-clara);
    max-width: 520px;
    margin-bottom: 2.5rem;
    font-weight: 300;
    line-height: 1.7;
  }

  .btn-primary {
    display: inline-block;
    padding: 0.875rem 2rem;
    background: var(--naranja);
    color: white;
    text-decoration: none;
    font-family: 'Rajdhani', sans-serif;
    font-weight: 600;
    font-size: 1rem;
    letter-spacing: 0.05em;
    transition: background 0.2s, transform 0.15s;
  }

  .btn-primary:hover {
    background: var(--naranja-suave);
    transform: translateY(-1px);
  }

  .btn-secondary {
    display: inline-block;
    padding: 0.875rem 2rem;
    border: 1px solid var(--plata);
    color: var(--plata-clara);
    text-decoration: none;
    font-family: 'Rajdhani', sans-serif;
    font-weight: 600;
    font-size: 1rem;
    letter-spacing: 0.05em;
    margin-left: 1rem;
    transition: border-color 0.2s, color 0.2s;
  }

  .btn-secondary:hover {
    border-color: var(--blanco);
    color: var(--blanco);
  }

  /* STATS */
  .stats {
    background: var(--oscuro);
    border-top: 1px solid rgba(139,144,153,0.12);
    border-bottom: 1px solid rgba(139,144,153,0.12);
    padding: 3rem 4rem;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 2rem;
  }

  .stat {
    text-align: center;
    padding: 1rem;
    border-right: 1px solid rgba(139,144,153,0.12);
  }

  .stat:last-child { border-right: none; }

  .stat-num {
    font-family: 'Rajdhani', sans-serif;
    font-size: 2.5rem;
    font-weight: 700;
    color: var(--naranja);
    line-height: 1;
    margin-bottom: 0.4rem;
  }

  .stat-label {
    font-size: 0.8rem;
    color: var(--plata);
    letter-spacing: 0.05em;
  }

  /* SECTIONS */
  section {
    padding: 6rem 4rem;
  }

  .section-header {
    margin-bottom: 3.5rem;
  }

  .section-tag {
    font-family: 'Rajdhani', sans-serif;
    font-size: 0.8rem;
    font-weight: 600;
    color: var(--naranja);
    letter-spacing: 0.15em;
    margin-bottom: 0.75rem;
  }

  .section-header h2 {
    font-family: 'Rajdhani', sans-serif;
    font-size: clamp(2rem, 4vw, 3rem);
    font-weight: 700;
    color: var(--blanco);
    line-height: 1.1;
  }

  .section-header p {
    margin-top: 1rem;
    color: var(--plata-clara);
    font-weight: 300;
    max-width: 540px;
    line-height: 1.7;
  }

  /* SERVICIOS */
  #servicios { background: var(--negro); }

  .servicios-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5px;
    background: rgba(139,144,153,0.15);
    border: 1px solid rgba(139,144,153,0.15);
  }

  .servicio {
    background: var(--negro);
    padding: 2.5rem;
    position: relative;
    overflow: hidden;
    transition: background 0.2s;
  }

  .servicio:hover { background: var(--oscuro); }

  .servicio::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px;
    height: 0;
    background: var(--naranja);
    transition: height 0.3s;
  }

  .servicio:hover::before { height: 100%; }

  .servicio-icon {
    font-size: 2rem;
    margin-bottom: 1.25rem;
    display: block;
  }

  .servicio h3 {
    font-family: 'Rajdhani', sans-serif;
    font-size: 1.25rem;
    font-weight: 600;
    color: var(--blanco);
    margin-bottom: 0.75rem;
  }

  .servicio p {
    font-size: 0.875rem;
    color: var(--plata);
    line-height: 1.65;
    font-weight: 300;
  }

  /* PROTOTIPOS */
  #prototipos { background: var(--oscuro); }

  .prototipos-layout {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: center;
  }

  .proto-visual {
    background: var(--medio);
    border: 1px solid rgba(139,144,153,0.15);
    padding: 3rem;
    position: relative;
  }

  .proto-visual::after {
    content: '';
    position: absolute;
    bottom: -8px;
    right: -8px;
    width: 100%;
    height: 100%;
    border: 1px solid rgba(26,111,232,0.3);
    z-index: -1;
  }

  .proto-list {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 1.25rem;
  }

  .proto-list li {
    display: flex;
    align-items: flex-start;
    gap: 1rem;
    padding-bottom: 1.25rem;
    border-bottom: 1px solid rgba(139,144,153,0.1);
  }

  .proto-list li:last-child { border-bottom: none; padding-bottom: 0; }

  .proto-num {
    font-family: 'Rajdhani', sans-serif;
    font-size: 1.5rem;
    font-weight: 700;
    color: var(--naranja);
    line-height: 1;
    flex-shrink: 0;
    width: 2rem;
  }

  .proto-list h4 {
    font-family: 'Rajdhani', sans-serif;
    font-size: 1rem;
    font-weight: 600;
    color: var(--blanco);
    margin-bottom: 0.25rem;
  }

  .proto-list p {
    font-size: 0.85rem;
    color: var(--plata);
    font-weight: 300;
    line-height: 1.6;
  }

  .impresion-3d-badge {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    background: rgba(26,111,232,0.12);
    border: 1px solid rgba(26,111,232,0.3);
    padding: 0.4rem 0.9rem;
    font-size: 0.8rem;
    color: var(--naranja-suave);
    font-family: 'Rajdhani', sans-serif;
    font-weight: 600;
    letter-spacing: 0.05em;
    margin-bottom: 1.5rem;
  }

  /* POR QUÉ NOSOTROS */
  #nosotros { background: var(--negro); }

  .razones-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
  }

  .razon {
    padding: 2rem;
    border: 1px solid rgba(139,144,153,0.12);
    display: flex;
    gap: 1.25rem;
    transition: border-color 0.2s;
  }

  .razon:hover { border-color: rgba(26,111,232,0.4); }

  .razon-icon {
    font-size: 1.5rem;
    flex-shrink: 0;
    margin-top: 0.2rem;
  }

  .razon h3 {
    font-family: 'Rajdhani', sans-serif;
    font-size: 1.1rem;
    font-weight: 600;
    color: var(--blanco);
    margin-bottom: 0.5rem;
  }

  .razon p {
    font-size: 0.875rem;
    color: var(--plata);
    line-height: 1.65;
    font-weight: 300;
  }

  /* CONTACTO */
  #contacto {
    background: var(--oscuro);
    border-top: 1px solid rgba(139,144,153,0.12);
  }

  .contacto-layout {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 5rem;
    align-items: start;
  }

  .contacto-info h2 {
    font-family: 'Rajdhani', sans-serif;
    font-size: clamp(2rem, 4vw, 3rem);
    font-weight: 700;
    color: var(--blanco);
    line-height: 1.1;
    margin-bottom: 1rem;
  }

  .contacto-info p {
    color: var(--plata-clara);
    font-weight: 300;
    line-height: 1.7;
    margin-bottom: 2rem;
  }

  .contacto-detalle {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .contacto-item {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    font-size: 0.9rem;
    color: var(--plata-clara);
  }

  .contacto-item span:first-child {
    color: var(--naranja);
    font-size: 1.1rem;
  }

  .form-group {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .form-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
  }

  input, textarea, select {
    width: 100%;
    background: var(--medio);
    border: 1px solid rgba(139,144,153,0.2);
    color: var(--blanco);
    padding: 0.875rem 1rem;
    font-family: 'Inter', sans-serif;
    font-size: 0.9rem;
    outline: none;
    transition: border-color 0.2s;
  }

  input:focus, textarea:focus, select:focus {
    border-color: var(--naranja);
  }

  input::placeholder, textarea::placeholder {
    color: var(--plata);
  }

  select option { background: var(--oscuro); }

  textarea { resize: vertical; min-height: 120px; }

  /* FOOTER */
  footer {
    background: var(--negro);
    border-top: 1px solid rgba(139,144,153,0.12);
    padding: 2rem 4rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  footer p {
    font-size: 0.8rem;
    color: var(--plata);
  }

  .footer-logo {
    font-family: 'Rajdhani', sans-serif;
    font-size: 1.1rem;
    font-weight: 700;
    color: var(--blanco);
  }

  .footer-logo span { color: var(--naranja); }

  /* DIVISOR */
  .divisor {
    width: 100%;
    height: 1px;
    background: linear-gradient(90deg, transparent, rgba(26,111,232,0.4), transparent);
    margin: 0;
  }

  /* WHATSAPP BTN */
  .whatsapp-btn {
    position: fixed;
    bottom: 2rem;
    right: 2rem;
    background: #25D366;
    border-radius: 50%;
    width: 60px;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 4px 15px rgba(37, 211, 102, 0.4);
    z-index: 999;
    transition: transform 0.2s, box-shadow 0.2s;
  }

  .whatsapp-btn:hover {
    transform: scale(1.1);
    box-shadow: 0 6px 20px rgba(37, 211, 102, 0.6);
  }

  /* RESPONSIVE */
  @media (max-width: 768px) {
    nav { padding: 1rem 1.5rem; }
    nav ul { display: none; }
    .hero { padding: 6rem 1.5rem 3rem; }
    .stats { grid-template-columns: repeat(2, 1fr); padding: 2rem 1.5rem; }
    .stat { border-right: none; border-bottom: 1px solid rgba(139,144,153,0.12); }
    section { padding: 4rem 1.5rem; }
    .servicios-grid { grid-template-columns: 1fr; }
    .prototipos-layout { grid-template-columns: 1fr; gap: 2rem; }
    .razones-grid { grid-template-columns: 1fr; }
    .contacto-layout { grid-template-columns: 1fr; gap: 3rem; }
    .form-row { grid-template-columns: 1fr; }
    footer { flex-direction: column; gap: 1rem; text-align: center; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="logo">Tornería<span>.</span>Arator</div>
  <ul>
    <li><a href="#servicios">Servicios</a></li>
    <li><a href="#prototipos">Prototipos</a></li>
    <li><a href="#nosotros">Nosotros</a></li>
    <li><a href="#contacto">Contacto</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-content">
    <div class="hero-eyebrow">Trabajos de precisión</div>
    <h1>Tornería de<br>alta <em>calidad</em><br>y prototipos 3D</h1>
    <p>Fabricamos piezas de precisión a las necesidades del cliente. Desde trabajos de tornería y fresado hasta prototipos e impresión 3D para proyectos industriales y creativos.</p>
    <a href="#contacto" class="btn-primary">Solicitar presupuesto</a>
    <a href="#servicios" class="btn-secondary">Ver servicios</a>
  </div>
</section>

<!-- STATS -->
<div class="stats">
  <div class="stat">
    <div class="stat-num">+10</div>
    <div class="stat-label">Años de experiencia</div>
  </div>
  <div class="stat">
    <div class="stat-num">500+</div>
    <div class="stat-label">Proyectos realizados</div>
  </div>
  <div class="stat">
    <div class="stat-num">100%</div>
    <div class="stat-label">Trabajos de precisión</div>
  </div>
  <div class="stat">
    <div class="stat-num">✓</div>
    <div class="stat-label">Cotización sin cargo</div>
  </div>
</div>

<div class="divisor"></div>

<!-- SERVICIOS -->
<section id="servicios">
  <div class="section-header">
    <div class="section-tag">Lo que hacemos</div>
    <h2>Servicios de fabricación<br>y mecanizado</h2>
    <p>Trabajamos con metales, plásticos y materiales especiales para industria, automotriz, agro y proyectos a medida.</p>
  </div>

  <div class="servicios-grid">
    <div class="servicio">
      <span class="servicio-icon">⚙️</span>
      <h3>Tornería paralela</h3>
      <p>Mecanizado en torno paralelo para piezas cilíndricas, roscas, ejes y componentes trabajados con experiencia y oficio.</p>
    </div>
    <div class="servicio">
      <span class="servicio-icon">🔩</span>
      <h3>Fresado</h3>
      <p>Fresado manual para superficies planas, ranuras, engranajes y geometrías trabajadas con criterio y experiencia.</p>
    </div>
    <div class="servicio">
      <span class="servicio-icon">🖨️</span>
      <h3>Impresión 3D</h3>
      <p>Prototipos 3D en PLA y PLA+. Ideal para validar diseños antes de fabricar en metal o para piezas funcionales.</p>
    </div>
    <div class="servicio">
      <span class="servicio-icon">📐</span>
      <h3>Prototipos a medida</h3>
      <p>Desde el plano o archivo 3D hasta la pieza terminada. Trabajamos con el cliente en cada etapa para asegurar que el prototipo cumpla su función.</p>
    </div>
    <div class="servicio">
      <span class="servicio-icon">🔧</span>
      <h3>Soldadura y armado</h3>
      <p>Soldadura TIG y electro. Armado de conjuntos mecánicos y estructuras metálicas con control de calidad en cada etapa.</p>
    </div>
    <div class="servicio">
      <span class="servicio-icon">📦</span>
      <h3>Series pequeñas</h3>
      <p>Producción de series cortas para industria y comercio. Cada pieza revisada y controlada antes de la entrega.</p>
    </div>
  </div>
</section>



<!-- POR QUÉ NOSOTROS -->
<section id="nosotros">
  <div class="section-header">
    <div class="section-tag">Por qué elegirnos</div>
    <h2>Experiencia, oficio<br>y compromiso</h2>
  </div>

  <div class="razones-grid">
    <div class="razon">
      <div class="razon-icon">🎯</div>
      <div>
        <h3>Trabajo cuidado</h3>
        <p>Cada pieza se revisa antes de entregarse. No sale del taller algo que no esté bien hecho.</p>
      </div>
    </div>
    <div class="razon">
      <div class="razon-icon">⚡</div>
      <div>
        <h3>Tiempos reales</h3>
        <p>Damos plazos que cumplimos. Si hay una urgencia, la evaluamos y damos una respuesta honesta antes de comprometernos.</p>
      </div>
    </div>
    <div class="razon">
      <div class="razon-icon">💬</div>
      <div>
        <h3>Comunicación directa</h3>
        <p>Hablás con quien hace el trabajo. Sin intermediarios, sin demoras en las respuestas, sin malentendidos en el pedido.</p>
      </div>
    </div>
    <div class="razon">
      <div class="razon-icon">🔬</div>
      <div>
        <h3>Herramientas y oficio</h3>
        <p>Torno paralelo, fresadora manual y equipos de impresión 3D para cubrir desde piezas simples hasta prototipos complejos.</p>
      </div>
    </div>
  </div>
</section>

<!-- CONTACTO -->
<section id="contacto">
  <div class="contacto-layout">
    <div class="contacto-info">
      <div class="section-tag">Contacto</div>
      <h2>Pedinos un<br>presupuesto<br>por WhatsApp</h2>
      <p>Contanos qué necesitás y te respondemos a la brevedad con un presupuesto sin compromiso.</p>
      <div class="contacto-detalle">
        <div class="contacto-item">
          <span>📍</span>
          <span>Buenos Aires, Argentina</span>
        </div>
        <div class="contacto-item">
          <span><svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="#25D366"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg></span>
          <span>+54 11 6249-9386</span>
        </div>
        <div class="contacto-item">
          <span>✉️</span>
          <span>torneria.arator@gmail.com</span>
        </div>
        <div class="contacto-item">
          <span>🕐</span>
          <span>Lunes a viernes, 8:00 – 18:00</span>
        </div>
      </div>
    </div>

    <div class="form-group">
      <div class="form-row">
        <input type="text" placeholder="Nombre">
        <input type="text" placeholder="Empresa (opcional)">
      </div>
      <input type="email" placeholder="Email">
      <input type="tel" placeholder="Teléfono">
      <select>
        <option value="" disabled selected>Tipo de trabajo</option>
        <option>Tornería paralela</option>
        <option>Fresado</option>
        <option>Impresión 3D</option>
        <option>Prototipo a medida</option>
        <option>Serie pequeña</option>
        <option>Otro</option>
      </select>
      <textarea placeholder="Describí brevemente qué necesitás: material, medidas, cantidad, uso final..."></textarea>
      <button type="button" class="btn-primary" style="border:none;cursor:pointer;width:100%;text-align:center;font-size:1rem;">Enviar consulta</button>
    </div>
  </div>
</section>

<!-- BOTON WHATSAPP -->
<a href="https://wa.me/541162499386" target="_blank" class="whatsapp-btn" title="Contactar por WhatsApp">
  <svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" viewBox="0 0 24 24" fill="white"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
</a>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">Tornería<span>.</span>Arator</div>
  <p>© 2026 Tornería Arator — Todos los derechos reservados</p>
  <p style="font-size:0.75rem;color:var(--plata)">Tornería y fresado manual</p>
</footer>

</body>
</html>
