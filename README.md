<div align="center">

<img src="public/images/logo.png" alt="Logo de BiblioGames" width="280" />

# BiblioGames

Biblioteca digital para la gestión y consulta online de un catálogo de videojuegos físicos de PC y Xbox.

[![Astro](https://img.shields.io/badge/Astro-7.2-BC52EE?style=for-the-badge&logo=astro&logoColor=white)](https://astro.build)
[![Node.js](https://img.shields.io/badge/Node.js-%3E%3D22.12-339933?style=for-the-badge&logo=node.js&logoColor=white)](https://nodejs.org)
[![JSON](https://img.shields.io/badge/Datos-JSON-000000?style=for-the-badge&logo=json&logoColor=white)](https://www.json.org)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/es/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/es/docs/Web/CSS)
[![GitHub Pages](https://img.shields.io/badge/Desplegado%20en-GitHub%20Pages-222222?style=for-the-badge&logo=github&logoColor=white)](https://pages.github.com)
[![License](https://img.shields.io/badge/Licencia-MIT-blue?style=for-the-badge)](#licencia)

</div>

---

## Descripción

**BiblioGames** es una aplicación web estática construida con [Astro](https://astro.build) que permite catalogar, organizar y consultar online una colección personal de videojuegos físicos de PC y Xbox. Cada juego se define como una ficha con portada, imagen de fondo, valoración, plataforma, formato, desarrollador, editora, géneros, temáticas, características, tamaño de descarga, resumen y galería de imágenes, además de soporte para expansiones y contenido descargable (DLC).

El diseño de la interfaz está inspirado en [Gameyfin](https://gameyfin.org), ofreciendo una experiencia visual moderna, con tarjetas de portada, páginas de detalle por juego y una navegación limpia orientada a la consulta rápida del catálogo.

## Características

- Catálogo de juegos gestionado mediante un único archivo `games.json`, sin necesidad de base de datos.
- Fichas de detalle individuales generadas automáticamente para cada juego (`/juego/[slug]`).
- Soporte para expansiones y DLC asociados a cada título.
- Diseño visual atractivo con portadas, fondos ambientados y galerías de imágenes.
- Sitio 100% estático, ligero y rápido, generado en tiempo de compilación con Astro.
- Despliegue automático mediante GitHub Actions a GitHub Pages.

## Estructura del proyecto

```text
bibliogames/
├── public/
│   ├── images/
│   │   ├── covers/            # Portadas verticales de cada juego
│   │   ├── covers-landscape/   # Imágenes de galería y DLC
│   │   └── background/         # Fondos de las fichas de detalle
│   ├── styles/                 # Hojas de estilo (Bootstrap, tema, etc.)
│   └── scripts/                # Scripts del tema (sliders, validaciones, etc.)
├── src/
│   ├── components/              # Header, Footer y componentes reutilizables
│   ├── data/
│   │   └── games.json           # Catálogo completo de juegos (fuente de datos)
│   ├── layouts/
│   │   └── Layout.astro         # Plantilla base de la web
│   └── pages/
│       ├── index.astro          # Página principal con el listado del catálogo
│       └── juego/[slug].astro   # Página de detalle dinámica por juego
├── astro.config.mjs
└── package.json
```

## Esquema de datos de un juego

Cada entrada de `src/data/games.json` sigue esta estructura:

```json
{
  "id": 1,
  "slug": "nombre-del-juego",
  "title": "Nombre del juego",
  "label": "Categoría o tipo",
  "license": "Plataforma de licencia (Steam, GOG, Uplay, Battle.net...)",
  "cover": "images/covers/PORTADA.webp",
  "background": "images/background/FONDO.webp",
  "year": 2024,
  "rating": 4.5,
  "platform": "PC | Xbox",
  "format": "Físico",
  "developer": "Estudio desarrollador",
  "publisher": "Editora",
  "genres": ["Género 1", "Género 2"],
  "themes": ["Temática 1", "Temática 2"],
  "features": ["Un jugador", "Multijugador"],
  "downloadSize": "XX GiB",
  "summary": "Descripción del juego.",
  "media": ["images/covers-landscape/1.webp"],
  "dlc": [
    {
      "title": "Nombre de la expansión",
      "year": 2024,
      "cover": "images/covers-landscape/DLC.webp",
      "downloadSize": "XX GiB"
    }
  ]
}
```

## Instalación y uso local

Requiere **Node.js 22.12** o superior.

```bash
# Clonar el repositorio
git clone https://github.com/rubenterre/bibliogames.git
cd bibliogames

# Instalar dependencias
npm install

# Servidor de desarrollo
npm run dev

# Construir versión de producción
npm run build

# Previsualizar la build
npm run preview
```

## Despliegue

El proyecto se despliega automáticamente en **GitHub Pages** mediante un workflow de GitHub Actions (`.github/workflows/deploy.yml`) que se ejecuta en cada push a la rama `main`. El sitio publicado está disponible en:

👉 **https://rubenterre.github.io/bibliogames**

## Licencia

Este proyecto se distribuye bajo licencia MIT. Los videojuegos, portadas y marcas mencionadas en el catálogo son propiedad de sus respectivos desarrolladores y editoras, y se usan únicamente con fines de catalogación personal.

---

<div align="center">
Hecho con ❤️ por <a href="https://rubenterre.me">Rubén Terre</a>
</div>
