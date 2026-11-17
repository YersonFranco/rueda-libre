# Rueda Libre — Tailwind CSS 4

Sitio web responsive para presentar los servicios de alquiler de bicicletas y recorridos guiados de Rueda Libre en Medellín. Esta versión adapta las tres páginas del proyecto a Tailwind CSS 4 mediante la CLI.

## Páginas

- `index.html`: presentación, servicios, beneficios y ubicación.
- `paginas/tarifas.html`: tarifas de alquiler y recorridos guiados.
- `paginas/reservas.html`: formulario con validación nativa del navegador.

## Tecnologías

- HTML5 semántico.
- Tailwind CSS 4 mediante `@tailwindcss/cli`.
- CSS generado y optimizado en `css/output.css`.
- Google Fonts: Montserrat y Open Sans.
- Imágenes locales en `img/`.

## Requisitos

- Node.js 20 o superior.
- npm.

## Instalación y ejecución

```bash
npm install
npm run dev
```

El comando `dev` observa los archivos HTML y `src/input.css`, y regenera `css/output.css` cuando detecta cambios. Para generar la hoja final optimizada:

```bash
npm run build
```

Después de compilar, abre `index.html` con Live Server o sirve la carpeta raíz con un servidor estático.

> `css/output.css` está incluido en el repositorio porque GitHub Pages publica archivos estáticos y no ejecuta la CLI. `node_modules/` se excluye mediante `.gitignore`.

## Estructura

```text
rueda-libre/
├── index.html
├── paginas/
│   ├── tarifas.html
│   └── reservas.html
├── src/
│   └── input.css
├── css/
│   └── output.css
├── img/
├── bitacora.txt
├── package.json
├── .gitignore
└── README.md
```

## Decisiones de diseño y framework

Se eligió Tailwind CSS porque Rueda Libre necesita una identidad visual propia y coherente en sus páginas, además de una interfaz adaptable a celulares, tabletas y escritorio. El enfoque utility-first permite construir componentes personalizados combinando utilidades de layout, espaciado, tipografía, color, bordes y estados.

La personalización de marca se centraliza en `src/input.css` mediante `@theme`: verde `ruta` (#1E7A4F), naranja `pedal` (#F39A2B), azul oscuro `noche` (#14213D), crema `crema` (#FAF6EF) y gris `asfalto` (#5B6470). Las fuentes de títulos y texto también se definen allí.

Como desventaja, las clases pueden hacer que el HTML sea extenso y Tailwind no incluye componentes interactivos prediseñados. Para mitigarlo, se mantienen patrones visuales consistentes, etiquetas semánticas, clases agrupadas por propósito y componentes sencillos reutilizables como tarjetas, botones y campos de formulario. Se evita abusar de `@apply` para conservar el enfoque utility-first.

El diseño es mobile-first: las clases sin prefijo aplican desde el tamaño base y los prefijos `sm:`, `md:` y `lg:` ajustan el diseño desde 640 px, 768 px y 1024 px, respectivamente.

## Accesibilidad y funcionamiento

- Un encabezado principal `h1` por página y jerarquía de títulos.
- Navegación identificada con `aria-label` y página actual marcada con `aria-current`.
- Imágenes con textos alternativos descriptivos.
- Etiquetas asociadas a los campos del formulario y validación HTML nativa.
- Estados visibles de `focus-visible` y enlaces descriptivos.
- Tablas con estructura semántica.
- Enlaces externos con `rel="noopener noreferrer"` cuando se abren en otra pestaña.

El formulario de reservas es una demostración académica. La validación ocurre en el navegador, pero no existe todavía un backend que almacene o procese solicitudes.

## Publicación en GitHub Pages

1. Sube el contenido del repositorio, incluyendo `css/output.css`.
2. No subas `node_modules/`.
3. En GitHub, entra a **Settings → Pages**.
4. Selecciona la rama `main` y la carpeta raíz (`/ root`) como origen.
5. Guarda y espera a que GitHub Pages publique el sitio.

Repositorio: https://github.com/YersonFranco/rueda-libre  
Sitio: https://yersonfranco.github.io/rueda-libre/

## Comparación breve: Bootstrap y Tailwind

Bootstrap ofrece componentes y estilos prediseñados que aceleran la construcción de interfaces convencionales. Tailwind ofrece utilidades de bajo nivel para definir directamente el diseño en el marcado y personalizar con precisión la identidad visual. Para esta versión de Rueda Libre se prioriza Tailwind por la flexibilidad de diseño y la consistencia de marca. La contrapartida es que el equipo debe construir y mantener sus propios patrones visuales y comportamientos.
