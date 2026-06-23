# KoenShell — Tienda de Componentes
## Briefing Técnico para Desarrollo Front-End

---

## ¿Qué es este proyecto?

Landing Page corporativa de una sola página (One-Page) para **KoenShell**, empresa mexicana dedicada a la venta de partes y componentes para computadoras de escritorio y laptops.

**La página NO es una tienda en línea.** No tiene carrito de compras ni pasarela de pagos.

**Lo que sí hace:**
- Presenta la propuesta de valor de KoenShell
- Muestra el catálogo de productos (imagen, nombre, descripción, precio referencial)
- Captura leads mediante un formulario de cotización
- Redirige al usuario a WhatsApp o correo para cerrar la venta manualmente

---

## Problemática del cliente

KoenShell operaba 100% por WhatsApp y redes sociales:
- Sin sitio web propio → no aparece en Google
- Catálogo compartido como imágenes o listas de texto sin precios actualizados
- Pedidos gestionados manualmente → errores, retrasos, pérdida de información
- Sin métricas de comportamiento de usuario ni datos de conversión
- Clientes potenciales elegían competidores con tienda en línea por falta de canal formal

---

## Solución propuesta

Landing Page estática (Front-End puro) que:
1. Establece presencia digital profesional para KoenShell
2. Presenta el catálogo con estructura visual clara
3. Captura solicitudes de cotización mediante formulario validado
4. Sirve como base para una Fase 2 con backend y producción (agosto 2026)

---

## Stack tecnológico

```
HTML5 semántico
CSS3 modularizado (sin frameworks)
JavaScript nativo (sin jQuery ni librerías externas)
Imágenes: .webp comprimido
Íconos: .svg vectoriales
```

**Sin backend en esta fase.** El formulario valida localmente con JS pero no persiste datos.

---

## Estructura de la página — 5 secciones en orden

```
┌─────────────────────────────────────┐
│  NAV — Menú sticky con anchor links │
├─────────────────────────────────────┤
│  1. HERO SECTION                    │
├─────────────────────────────────────┤
│  2. BENEFICIOS                      │
├─────────────────────────────────────┤
│  3. PRUEBAS SOCIALES                │
├─────────────────────────────────────┤
│  4. FORMULARIO DE COTIZACIÓN        │
├─────────────────────────────────────┤
│  5. FOOTER                          │
└─────────────────────────────────────┘
```

### NAV
- Logo o nombre KoenShell a la izquierda
- Links de navegación a la derecha: Inicio | Beneficios | Testimonios | Contacto
- Sticky (fijo al hacer scroll)
- En mobile: menú hamburguesa desplegable
- Navegación con smooth scroll a cada sección via anchor links

---

### 1. Hero Section
- Fondo: video corto `.mp4` con autoplay, muted, loop (cinemagraph — LEDs RGB parpadeando en gabinete, resto estático)
- Overlay semitransparente oscuro sobre el video para legibilidad del texto
- H1: propuesta de valor principal de KoenShell
- Subtítulo breve
- Botón CTA secundario: "Ver catálogo" → anchor link a sección Beneficios

---

### 2. Beneficios
- Grid de 3 o 4 tarjetas
- Cada tarjeta: ícono SVG + título + descripción corta (2-3 líneas)
- Contenido sugerido:
  - Stock disponible y actualizado
  - Precios claros sin sorpresas
  - Atención rápida y profesional
  - Envío o entrega ágil
- **CTA PRINCIPAL** al final de esta sección: botón "Solicitar cotización ahora" → anchor link a formulario
- Separador entre secciones con forma curva (clip-path o SVG wave)

---

### 3. Pruebas Sociales
- 2 o 3 tarjetas de testimonio: foto de avatar (placeholder), nombre, texto del testimonio
- Contador de pedidos completados (número estático, sin animación compleja)
- Fondo de sección diferenciado: `#E8EAF6`

---

### 4. Formulario de Cotización
- Campos:
  - Nombre completo (required)
  - Correo electrónico (required, validar formato)
  - Teléfono (required, solo números, mínimo 10 dígitos)
  - Producto de interés (select o input text)
  - Mensaje (textarea, opcional)
- Botón: "Enviar solicitud"
- Validación en tiempo real con JS nativo:
  - Borde rojo + mensaje de error si formato inválido
  - Borde verde si correcto
- Al enviar: mostrar mensaje de confirmación en pantalla (no redirigir, no recargar)
- No conecta a backend en esta fase

---

### 5. Footer
- Nombre / logo KoenShell
- Íconos de redes sociales (SVG): Facebook, Instagram, WhatsApp
- Datos de contacto: correo y teléfono de KoenShell
- Texto de copyright: © 2026 KoenShell. Todos los derechos reservados.
- Link a aviso de privacidad (puede ser placeholder)

---

## Sistema de diseño

### Colores
```css
--color-primario:    #1A237E;  /* Azul marino — confianza, tecnología */
--color-secundario:  #546E7A;  /* Gris tecnológico — precisión, solidez */
--color-base:        #FFFFFF;  /* Blanco — claridad, legibilidad */
--color-fondo-alt:   #E8EAF6;  /* Azul muy claro — secciones alternas */
--color-texto:       #000000;  /* Negro — texto general */
--color-error:       #D32F2F;  /* Rojo — validación negativa */
--color-exito:       #388E3C;  /* Verde — validación positiva */
```

### Tipografía
```css
/* Importar desde Google Fonts */
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@700&family=Open+Sans:wght@400;600&display=swap');

--font-titulo:  'Montserrat', sans-serif;   /* H1, H2, botones */
--font-cuerpo:  'Open Sans', sans-serif;    /* Párrafos, labels, inputs */
```

### Escala tipográfica
```
H1 desktop:   48px / Montserrat Bold
H1 mobile:    32px / Montserrat Bold
H2:           32px desktop / 24px mobile / Montserrat Bold
H3:           22px / Montserrat Bold
Cuerpo:       16px / Open Sans Regular
Label:        14px / Open Sans SemiBold
Botón:        16px / Montserrat Bold / UPPERCASE
```

### Botones
```
CTA Primario:
  background: #1A237E
  color: #FFFFFF
  border: none
  border-radius: 4px
  padding: 14px 32px
  font: Montserrat Bold 16px uppercase

CTA Secundario:
  background: transparent
  color: #FFFFFF
  border: 2px solid #FFFFFF
  border-radius: 4px
  padding: 12px 30px
  font: Montserrat Bold 16px uppercase
```

### Estilo de diseño
- **Flat Design** en elementos funcionales: botones, formulario, tarjetas de producto
- **Diseño orgánico** en separadores entre secciones: clip-path curvo o SVG wave en color `#E8EAF6`
- Sin sombras excesivas ni texturas complejas
- Tarjetas con `border-radius: 8px` y sombra sutil: `box-shadow: 0 2px 8px rgba(0,0,0,0.08)`

---

## Responsive — breakpoints

```css
/* Mobile first */
/* Base: 360px+ (móvil) */

@media (min-width: 768px) {
  /* Tablet */
}

@media (min-width: 1280px) {
  /* Desktop */
}
```

### Comportamiento por sección en mobile
- NAV: hamburguesa, menú desplegable vertical
- Hero: texto centrado, botón a ancho completo
- Beneficios: tarjetas en columna única
- Pruebas sociales: tarjetas en columna única
- Formulario: campos a ancho completo, stacked
- Footer: todo centrado, columna única

---

## Restricciones técnicas

- Peso total < 5 MB
- Carga inicial < 800 KB
- Sin frameworks CSS (no Bootstrap, no Tailwind)
- Sin librerías JS externas
- Compatible: Chrome v110+, Firefox v115+, Safari v16+, Edge v110+
- NO compatible con Internet Explorer
- Sin backend, sin base de datos, sin CMS en esta fase

---

## Lo que NO hace esta página

- No procesa pagos
- No tiene carrito de compras
- No guarda datos del formulario en ninguna base de datos
- No tiene panel de administración
- No tiene buscador de productos
- No tiene sistema de inventario en tiempo real

Todo esto corresponde a la **Fase 2** del proyecto (agosto 2026).

---

## Archivos sugeridos

```
/
├── index.html
├── css/
│   ├── reset.css
│   ├── variables.css
│   ├── nav.css
│   ├── hero.css
│   ├── beneficios.css
│   ├── testimonios.css
│   ├── formulario.css
│   └── footer.css
├── js/
│   ├── nav.js          (hamburguesa + smooth scroll)
│   └── formulario.js   (validación en tiempo real)
├── assets/
│   ├── video/
│   │   └── hero-cinemagraph.mp4
│   ├── img/
│   │   └── (imágenes de productos en .webp)
│   └── icons/
│       └── (íconos SVG)
└── README.md
```
