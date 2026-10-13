# P-gina-web-Autolavado-GT-ELOHIM

Página web diseñada para dar a conocer la información del negocio **Autolavado GT ELOHIM**.

Repositorio público del proyecto: entregables en HTML y CSS.

> Sitio web desarrollado para **Autolavado GT ELOHIM** (Bucaramanga, Santander), optimizado para dispositivos móviles y enfocado en mostrar los servicios y facilitar el contacto directo con los clientes.

---

## Enlaces del proyecto

- 📁 **Repositorio:** [[Enlace a tu repositorio público de GitHub](https://github.com/Mari-Reyes/P-gina-web-Autolavado-GT-ELOHIM.git)]

---

## 1. El proyecto

- **Negocio:** Autolavado GT ELOHIM, centro de autodetailing para motocicletas, automóviles y camionetas. Está ubicado en la Calle 45 5W - 47, barrio Campo Hermoso, Bucaramanga, Santander.
- **Público objetivo:** Propietarios de motocicletas, automóviles y camionetas de Bucaramanga que buscan un lavado y detallado profesional, con precios claros según el tipo de vehículo.
- **Necesidad del cliente:** Contar con un sitio web propio donde los clientes puedan conocer el negocio, consultar los servicios con sus precios, ver los horarios y la ubicación, mirar videos del proceso y del resultado, reservar una cita y llegar fácilmente a sus redes sociales (Facebook, Instagram y TikTok).

### Páginas del sitio

| Archivo | Contenido |
|---|---|
| `index.html` | Inicio: quiénes somos, meta, resumen de servicios, métodos de pago, testimonios, horarios y mapa. |
| `segunda_pagina.html` | Servicios: lista de precios de motos, automóviles y camionetas, y video del proceso. |
| `tercera_pagina.html` | Contacto: datos del negocio, redes sociales, video del resultado, mapa y formulario de reserva de cita. |

---

## 2. Estructura

### Estructura de archivos

```text
P-gina-web-Autolavado-GT-ELOHIM/
├── index.html
├── segunda_pagina.html
├── tercera_pagina.html
├── README.md
├── CSS/
│   └── styles.css
├── fonts/
│   ├── Sora-VariableFont_wght.ttf
│   └── GoogleSans-VariableFont_GRAD_opsz_wght.ttf
├── images/
├── video/
│   ├── Proceso.mp4
│   └── Resultado.mp4
└── capturas/
```

### Justificación de Etiquetas Semánticas

- **`<nav>`**: contiene el menú que permite moverse entre las tres páginas. La página donde está el usuario se marca con "Estas aqui".
- **`<header>`**: contiene el logotipo del negocio en todas las páginas y, en servicios y contacto, el título y la introducción de la página.
- **`<main>`**: delimita el contenido central de cada página: los testimonios (inicio), el título y la lista de servicios (servicios) y los datos de contacto (contacto).
- **`<section>`**: agrupa por temas los bloques principales: sobre nosotros y meta, servicios, horarios, redes sociales y videos.
- **`<article>`**: contiene bloques con sentido propio, como "Quiénes somos" y el collage de fotos de servicios.
- **`<aside>`**: contiene los métodos de pago, que son información complementaria al resto de la página.
- **`<blockquote>`, `<cite>`, `<abbr>` y `<mark>`**: dan significado a los testimonios, a la dirección, a la abreviatura "Testimonios" y a la calificación destacada.
- **`<table>`**: muestra los horarios de atención en filas y columnas.
- **`<video>` y `<form>`**: el primero reproduce los videos de la carpeta `video/` y el segundo recibe la reserva de citas.
- **`<footer>`**: ubicado al final, incluye los derechos de autor.

---

## 3. Sistema Visual

### Variables CSS (`:root`)

```css
:root {
  --fondo: #000000;
  --banda: #ffffff;
  --tinta: #111111;
  --tarjeta: #1d0f0f;
  --borde: #4a2323;
  --texto: #ffffff;

  --principal: #961616;
  --principal-hover: #b81d1d;
  --acento: #c62a2a;
  --enlace: #ff7b7b;

  --fuente-titulos: "Sora", "Segoe UI", Arial, sans-serif;
  --fuente-texto: "Google Sans", "Segoe UI", Arial, sans-serif;
}
```

### Justificación del Diseño

**Colores:** Se eligió un fondo negro con letras blancas para transmitir la imagen de brillo y alta gama que busca un servicio de detallado. El menú y algunas franjas son blancos para alternar el ritmo de la página y separar las secciones. El rojo `#961616` es el color de acento de los botones y llamados a la acción, y se usa junto a `#3f1212` en el degradado de tres colores del pie de página (`#961616`, `#3f1212`, `#961616`). Sobre fondo negro se usa un rojo más claro (`#ff7b7b`) en los enlaces para que se lean bien.

**Tipografías:** Los títulos, el menú y los botones usan **Sora**, una fuente geométrica y ancha que da personalidad al negocio. Los párrafos, listas y formularios usan **Google Sans**, una fuente sans-serif limpia que se lee con facilidad en celulares. Ambas se cargan desde archivos locales con `@font-face` y `font-display: swap`, así el texto se ve mientras la fuente termina de cargar.

---

## 4. Especificidad (Conflictos Reales)

### Conflicto 1: Barra roja bajo los títulos

- **Regla A:** `h2::after` → Especificidad: (0, 0, 2). Dibuja la barra roja bajo cada título.
- **Regla B:** `.tarjeta-texto1 h2::after` → Especificidad: (0, 1, 2). Oculta esa barra con `display: none`.
- **Resultado:** Gana la Regla B por tener una clase más. Así, el título dentro de la tarjeta roja no muestra la barra, que no se vería sobre el fondo rojo.

📸 Captura: `capturas/especificidad-1.png`

### Conflicto 2: Altura de las imágenes (estilo en línea frente a `!important`)

- **Regla A:** `style="max-width: 100%; height: auto;"` escrito en la etiqueta `<img>` del HTML → Especificidad: (1, 0, 0, 0), la más alta de las declaraciones normales.
- **Regla B:** `body > section:has(> .tarjeta-texto1) > img { height: 100% !important; }` → Especificidad: (0, 1, 3).
- **Resultado:** Gana la Regla B porque `!important` tiene prioridad sobre cualquier declaración normal, incluso sobre el estilo en línea. Así la foto ocupa toda la altura de las dos tarjetas de texto sin modificar el HTML.

📸 Captura: `capturas/especificidad-2.png`

### Conflicto 3: Resolución por Orden (Empate de Especificidad)

- **Regla A:** `main > section img { height: 300px !important; }` → Especificidad: (0, 0, 3).
- **Regla B:** `@media (max-width: 900px) { main > section img { height: 240px !important; } }` → Especificidad: (0, 0, 3).
- **Resultado:** Al tener la misma especificidad, se aplica la Regla B porque aparece escrita después en la hoja de estilos (`styles.css`). Por eso las fotos de servicios bajan de 300px a 240px en pantallas de 900px o menos, y a 200px en pantallas de 600px o menos.

📸 Captura: `capturas/especificidad-3.png`

---

## 5. Herencia en CSS

**Propiedad heredada (`color` / `font-family`):**

Se definieron `font-family` y `color` en la regla del `body`, y los párrafos, listas y etiquetas del formulario las heredaron sin repetirlas. Los títulos solo cambian la fuente con `font-family: var(--fuente-titulos)`.

Las variables CSS también se heredan. En las franjas blancas se redefine `--texto: var(--tinta)`, y todos los hijos que usan `color: var(--texto)` (títulos, párrafos y etiquetas) pasan a letra oscura automáticamente, sin escribir una regla para cada uno.

**Propiedad no heredada (`border` / `padding` / `margin` / `background`):**

Se aplicó `padding: 64px` a cada `<section>`, pero los elementos hijos (títulos, párrafos e imágenes) no heredaron ese espacio interior y mantienen el suyo. Lo mismo ocurre con `background`: la franja blanca no pinta de blanco a las tarjetas oscuras que están dentro de ella.

---

## 6. Modelo de Cajas

### Cálculo del Ancho Total de un Componente

**Componente:** `.tarjeta-servicio` (tarjeta de cada servicio)

- Ancho mínimo de la columna de la cuadrícula: `minmax(260px, 1fr)` → **260px**
- Padding: 24px (izquierda) + 24px (derecha) = 48px
- Border: 5px (izquierda) + 1px (derecha) = 6px
- Se usa `box-sizing: border-box` en todos los elementos (`* { box-sizing: border-box; }`), por lo que el ancho total real es **260px** y el contenido ocupa 260px − 48px − 6px = **206px**.
- Sin `border-box` habría que declarar `width: 206px` para obtener los mismos 260px, y el cálculo sería 206px + 48px + 6px = 260px.

### Solapamiento de Márgenes (Margin Collapse)

En "Quiénes somos", el último párrafo de `.tarjeta-texto4` tiene `margin-bottom: 10px` y el formulario que le sigue tiene `margin-top: 28px`. Como `.tarjeta-texto4` no tiene padding ni borde, el margen del párrafo se solapa con el del formulario y el espacio real entre ambos es de **28px** (el valor mayor) en lugar de sumarse a 38px.

---

## 7. Selectores (Pseudoclases Estructurales)

**Pseudoclases analizadas:** `:nth-child(5):last-child` y `:first-child`

**Funcionamiento:**

- `.collage2 > :nth-child(5):last-child` evalúa los hijos del collage de fotos y selecciona el elemento que es, a la vez, el quinto y el último. Es decir, solo se aplica cuando hay exactamente 5 fotos. En ese caso la última foto ocupa 2 columnas (`grid-column: span 2`) y no queda un hueco vacío en la cuadrícula.
- `main > section > img:first-child` selecciona la primera imagen de la lista de servicios para quitarle el margen superior que sí llevan las demás imágenes (las de automóviles y camionetas).
- `body > form label:first-of-type` selecciona la primera etiqueta del formulario de reserva para que no tenga margen superior.

Además se usó la pseudoclase relacional `:has()` para elegir bloques por su contenido, por ejemplo `body > section.contenedor-video` y `body > section:has(> table)` para las franjas de video y de horarios.

---

## 8. Responsive Design (@media)

**Breakpoints:** `@media (max-width: 900px)` para tablets y `@media (max-width: 600px)` para celulares.

**Cambios aplicados:**

- **Hasta 900px:**
  - La sección "sobre nosotros" pasa de dos columnas a una.
  - El collage de fotos pasa de 5 columnas a 2.
  - Los testimonios pasan de 3 columnas a una sola.
  - Las tarjetas de dirección y teléfono se apilan.
  - Las fotos reducen su altura.
- **Hasta 600px:**
  - Los títulos principales bajan de 2.4rem a 1.8rem y los de sección de 2rem a 1.6rem.
  - El menú reduce su relleno y el tamaño de letra para que quepan sus tres enlaces.
  - Las secciones reducen su espacio vertical de 64px a 44px.
  - La lista de servicios pasa a una sola columna.
  - El mapa baja de 450px a 320px de alto.
- **En todos los tamaños:** las imágenes y los videos usan `width: 100%`, y el mapa usa `width: 100%` en CSS, que prevalece sobre el `width="600"` del HTML.

---

## 9. Problemas y Soluciones

**Problema 1:** Las imágenes no aparecían en la página.

- **Causa:** El nombre o la ruta del archivo en el HTML no coincidía exactamente con el archivo real (mayúsculas, extensión o carpeta). Por ejemplo, el logo se llama `Logo.png` y el póster del video lo busca como `logo.png`; en GitHub Pages, que distingue mayúsculas, uno de los dos no carga.
- **Solución:** Se revisaron los nombres exactos de los archivos de la carpeta `images/` y se verificó en la pestaña **Network** de las herramientas del navegador (F12) cuáles daban error 404.

**Problema 2:** La lista de servicios se desordenaba y se veía muy anidada.

- **Causa:** Varias listas `<ol>` y etiquetas `<div>` quedaron sin cerrar en el HTML, y el navegador las anidó unas dentro de otras.
- **Solución:** Se aplicó `display: contents` a los `<ol>` en CSS. Así desaparecen del diseño y las tarjetas se acomodan en una sola cuadrícula, sin modificar el HTML.

**Problema 3:** Las fuentes personalizadas no se cargaban.

- **Causa:** El enlace de Google Fonts del `<head>` estaba cortado, así que el navegador nunca descargaba las tipografías.
- **Solución:** Se usaron los archivos `.ttf` del proyecto con `@font-face`, declarando el rango de pesos de cada fuente variable.

**Problema 4:** Los videos no se mostraban con el tamaño adecuado.

- **Causa:** El `<video>` no tenía dimensiones definidas y los estilos de la sección de video dependían de la posición de la sección. En la página de contacto hay dos `<section>`, y esas reglas dejaron de aplicarse.
- **Solución:** Se estilaron por clase (`.contenedor-video` y `.video-responsive`) con `width: 100%`, `max-width`, `aspect-ratio` y `max-height`. El video ahora se ve completo en escritorio y celular, y los selectores no dependen del orden de las secciones.

**Problema 5:** Un estilo pensado para una sección se aplicaba a otra.

- **Causa:** Se seleccionaban las secciones por su posición (`:first-of-type`, `:nth-of-type`, `:only-of-type`). Al agregar una segunda `<section>` en la página de contacto, las reglas cambiaron de destino.
- **Solución:** Se pasó a seleccionar por contenido con `:has()`, por ejemplo `body > section:has(> table)` para los horarios.

