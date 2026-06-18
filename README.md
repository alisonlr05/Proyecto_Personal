# Portafolio Personal — Alison López Reyes

**Curso:** IF7102 Multimedios | I Ciclo 2026 | UCR — Sede Regional de Guanacaste, Recinto de Liberia  
**Opción:** Opción 1 — Portafolio Multimedia Personal  
**Estudiante:** Alison Sofía López Reyes  
**Framework:** Vue 3 (Composition API + `<script setup>`)  
**Deploy:** https://alisonlr05.github.io/Proyecto_Personal/

---

## Descripción

Sitio de presentación profesional personal desarrollado con Vue 3 y Vite. Incluye secciones de presentación con foto y audio de autopresentación, galería de proyectos, habilidades técnicas con animaciones, video de introducción y sección de contacto. Soporta modo claro y oscuro.

---

## Estructura del proyecto

```
src/
├── main.js
├── App.vue                  # Componente raíz — fetch del JSON y toggle de tema
└── componentes/
    ├── Header.vue           # Navegación fija con burbuja animada y toggle de tema
    ├── HeroSection.vue      # Sección de bienvenida con íconos flotantes
    ├── About.vue            # Foto, descripción, audio y video de presentación
    ├── Skills.vue           # Grid de habilidades técnicas con animación SVG
    ├── Gallery.vue          # Tarjetas de proyectos con overlay y filtro de imagen
    └── Contacto.vue         # Links de contacto y redes sociales

public/
├── data/datos.json          # Datos del portafolio (perfil, habilidades, proyectos)
├── imagenes/                # imagenes para los proyectos y perfil, 
├── audio/presentacion.mp3
└── video/intro.mp4
```

---

## Cómo ejecutar el proyecto

### Instalación y desarrollo

```bash
# Clonar el repositorio
git clone https://github.com/alisonlr05/Proyecto_Personal.git
cd Proyecto_Personal

# Instalar dependencias
pnpm install
# o con npm:
npm install

# Levantar servidor de desarrollo
pnpm dev
# o con npm:
npm run dev
```

Abrir el navegador en `http://localhost:5173`

### Build y deploy

```bash
# Generar versión de producción
pnpm run build

# Deploy a GitHub Pages
pnpm run deploy
```

---

## IDE recomendado

[VS Code](https://code.visualstudio.com/) + extensión [Vue (Official / Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.volar)

Para depuración en el navegador:
- [Vue DevTools para Chrome](https://chromewebstore.google.com/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
- [Vue DevTools para Firefox](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
