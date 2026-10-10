# P-gina-web-Autolavado-GT-ELOHIM
Página web diseñada para dar a conocer información del negocio.

Nombre de tu negocio sitio web

Repositorio público del proyecto entregables en HTML y CSS
> Sitio web desarrollado para [Nombre del Negocio Local], optimizado para dispositivos móviles y enfocado en la conversión y contacto directo.

---

Enlaces del proyecto

- 🔗 **Sitio Web (GitHub Pages):** [Agrega tu enlace aquí si lo desplegaste]
- 📁 **Repositorio:** [Enlace a tu repositorio público de GitHub]

---

1. El proyecto

- **Negocio:** [Ejemplo: Panadería La Espiga / Taller de Motos Rápido]
- **Público Objetivo:** [Ejemplo: Vecinos del barrio, jóvenes de 18-40 años que buscan pedir a domicilio por WhatsApp, etc.]
- **Necesidad del Cliente:** [Explica la problemática que resuelve el sitio web, por ejemplo: El cliente solo vendía por WhatsApp e Instagram y perdía ventas por no mostrar su menú, precios ni ubicación clara.]

---

2.  Estructura

Estructura de archivos
```text
nombre-del-negocio/
├── index.html
├── segunda-pagina.html
├── README.md
├── css/
│   └── styles.css
├── images/
├── video/
└── capturas/

Justificación de Etiquetas Semánticas

- **<header>** y **<nav>**: Contienen el logotipo principal y la barra de navegación que permite moverse entre las dos páginas de forma fluida.

- **<main>**: Delimita el contenido central único de cada página para mejorar la accesibilidad y SEO.

- **<section>** y **<article>**: Agrupan temáticamente los bloques principales (servicios, testimonios, ubicación) y cada una de las tarjetas individuales de productos/servicios.

**<footer>**: Ubicado al final para incluir derechos de autor, enlaces secundarios y redes sociales.



3.  Sistema Visual
Variables CSS (:root)

:root {
  --color-principal: #2B2D42;
  --color-secundario: #8D99AE;
  --color-acento: #D90429;
  --color-fondo: #F8F9FA;
  --fuente-titulo: 'Shrikhand', cursive;
  --fuente-cuerpo: 'Inter', sans-serif;
  --espacio-base: 1rem;
}

Justificación del Diseño
Colores: [Explica por qué los elegiste; ej. Se seleccionó una paleta de tonos oscuros combinados con un color de acento llamativo para destacar los botones de acción].

Tipografías: [Explica la tipografía; ej. Se usó una fuente llamativa para los títulos que refleja la personalidad del negocio y una fuente sans-serif limpia para garantizar una lectura ágil en celulares].



4. Especificidad (Conflictos Reales)
Conflicto 1: Color del precio en tarjetas de oferta
Regla A: .tarjeta p → Especificidad: (0, 1, 1)

Regla B: .tarjeta--promo .precio → Especificidad: (0, 2, 0)

Resultado: Gana la Regla B por tener 2 clases frente a 1 clase y 1 etiqueta.

📸 Captura:

Conflicto 2: Estilo de botones de contacto
Regla A: main .btn → Especificidad: (0, 1, 1)

Regla B: .contacto__btn-enviar → Especificidad: (0, 1, 0)

Resultado: Gana la Regla A por tener 1 clase y 1 etiqueta frente a 1 sola clase.

📸 Captura:

Conflicto 3: Resolución por Orden (Empate de Especificidad)
Regla A: .menu__link → Especificidad: (0, 1, 0)

Regla B: .menu__link--activo → Especificidad: (0, 1, 0)

Resultado: Al tener la misma especificidad, se aplica la Regla B porque aparece escrita después en la hoja de estilos (styles.css).

📸 Captura:



5. Herencia en CSS
Propiedad Heredada (color / font-family):

Se definió font-family en la regla del body y todos los elementos hijos (párrafos, listas y encabezados) la heredaron automáticamente sin necesidad de repetirla.

Propiedad No Heredada (border / padding / margin):

Se aplicó un padding: 2rem a una <section>, pero los elementos hijos dentro de ella no heredaron dicho espacio interior, manteniendo su propio modelo de cajas.



6. Modelo de Cajas
Cálculo del Ancho Total de un Componente
Componente: .tarjeta-producto

Ancho del contenido (width): 300px

Padding: 15px (izquierda) + 15px (derecha) = 30px

Border: 2px (izquierda) + 2px (derecha) = 4px

Ancho Total Real: 300px + 30px + 4px = 334px (al no usar box-sizing: border-box).

Solapamiento de Márgenes (Margin Collapse)
El margin-bottom: 20px del título <h2> y el margin-top: 15px del primer párrafo <p> se solapan, resultando en un espacio real de 20px entre ellos (el valor mayor) en lugar de sumarse a 35px.

7. Selectores (Pseudoclases Estructurales)
Pseudoclase analizada: :nth-child(even) o :nth-child(2n)

Funcionamiento: Evalúa todos los elementos hermanos dentro de un mismo contenedor padre. Cuenta el orden de cada hijo y aplica los estilos únicamente a los elementos que ocupan posiciones pares (2, 4, 6...), permitiendo alternar colores de fondo entre filas o tarjetas.

8. Responsive Design (@media)
Breakpoint: @media (max-width: 768px)

Cambios aplicados:

La navegación cambia de alineación horizontal a un menú apilado verticalmente.

Las rejillas y columnas pasan a una sola columna para adaptarse cómodamente a pantallas de 360 px de ancho sin generar desbordamiento horizontal.

Los tamaños de letra de los títulos principales disminuyen de 2.5rem a 1.8rem.

9. Problemas y Soluciones
Problema 1: Desbordamiento horizontal en celulares (pantalla a 360px).

Causa: Las imágenes y tablas tenían un ancho fijo en píxeles que superaba el ancho del dispositivo.

Solución: Se agregó max-width: 100% y height: auto a las imágenes, y se envolvió la tabla en un contenedor con overflow-x: auto.

Problema 2: El mapa/video en iframe no se adaptaba al ancho de la pantalla.

Causa: El atributo width="600" en HTML forzaba un ancho fijo.

Solución: Se removieron las dimensiones fijas del HTML y se controló desde CSS con width: 100% y aspect-ratio: 16 / 9.

10. Capturas de Pantalla
Vista Escritorio
Inicio (index.html)
Segunda Página (contacto.html / servicios.html)
Vista Móvil (360px de ancho)
Inicio (index.html)
Segunda Página (contacto.html / servicios.html)