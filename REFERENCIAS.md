# REFERENCIAS.md
**Curso:** IF7102 Multimedios | I Ciclo 2026 | UCR  
**Proyecto:** Opción 1 — Portafolio Multimedia Personal  
**Estudiante:** Alison Sofía López Reyes  
**Framework:** Vue 3

---

## 1. Aprendizaje del Framework — Vue 3

| Recurso | URL | Uso |
|---|---|---|
| Vue.js — Introducción oficial | https://vuejs.org/guide/introduction.html | Entender qué es Vue 3 y su arquitectura |
| Vue.js — Quick Start | https://vuejs.org/guide/quick-start.html | Crear el proyecto base con `npm create vue@latest`, instalar dependencias y levantar el servidor de desarrollo |
| Vue.js — Composition API FAQ | https://vuejs.org/guide/extras/composition-api-faq.html | Decidir usar `<script setup>` con Composition API en lugar de Options API |
| Vue.js — Componentes y Props | https://vuejs.org/guide/components/props.html | Pasar datos del componente padre (`App.vue`) a los componentes hijo usando `defineProps` |
| Vue.js — Eventos de componentes | https://vuejs.org/guide/components/events.html | Emitir el evento `toggleTema` desde `Header.vue` hacia `App.vue` con `defineEmits` |
| Vue.js — `v-for` | https://vuejs.org/guide/essentials/list.html | Renderizar la lista de habilidades en `Skills.vue` y la lista de proyectos en `Gallery.vue` |
| Vue.js — `ref` y reactividad | https://vuejs.org/guide/essentials/reactivity-fundamentals.html | Manejar estado reactivo: `cargando`, `temaOscuro`, `audioReproduciendo`, etc. |
| Vue.js — Ciclo de vida (`onMounted`) | https://vuejs.org/guide/essentials/lifecycle.html | Cargar el JSON con `fetch` al montar el componente y posicionar la burbuja del nav |
| Vue.js — `watch` | https://vuejs.org/guide/essentials/watchers.html | Observar el estado `temaOscuro` para agregar/quitar la clase `tema-oscuro` en `document.body` |
| Vue.js — Template refs | https://vuejs.org/guide/essentials/template-refs.html | Acceder a elementos del DOM desde el script (`burbujaEl`, `itemsEl`) para la animación del nav |
| Vite — Documentación oficial | https://vite.dev/config/ | Configurar `vite.config.js` con el plugin de Vue y la base para GitHub Pages |

---

## 2. Diseño y recursos visuales

| Recurso | URL | Uso |
|---|---|---|
| Realtime Colors | https://www.realtimecolors.com/?colors=471010-ffffff-6c533d-a1b5a1-7d545a&fonts=Inter-Inter | Probar y definir la paleta de colores (marrones, verdes y beige) y la tipografía |
| Google Fonts | https://fonts.google.com/ | Explorar y seleccionar las fuentes: Playfair Display, DM Sans y Jost |
| Figma — Ejemplos de portafolios | https://www.figma.com/es-la/resource-library/ejemplos-sitios-portafolio/ | Explorar referencias visuales para definir la estructura y estética del portafolio |
| UX Folio Blog — Portfolio Examples | https://blog.uxfol.io/professional-portfolio/ | Ejemplos adicionales de portafolios profesionales y buenas prácticas de presentación |
| Atoms.dev | https://atoms.dev/dashboard | Traducir ideas propias a un borrador visual del portafolio |
| CodePen — Trending | https://codepen.io/trending | Explorar animaciones y efectos CSS/JS para incorporar en el proyecto |
| UIverse | https://uiverse.io/ | Explorar elementos de UI y animaciones reutilizables |
| CodePen — Keyframers (burbuja de nav) | https://codepen.io/team/keyframers/pen/xvoBrx | Referencia base para la animación de la burbuja que sigue al ítem activo en el header |
| CodePen — SultanKhanCQ (cards de skills) | https://codepen.io/SultanKhanCQ/pen/qEEZRmN | Referencia para el efecto de marco SVG animado con `stroke-dasharray` en las cards de habilidades |
| Lucide Icons | https://lucide.dev/ | Librería de íconos SVG usada a través de `lucide-vue-next` |

---

## 3. Recursos multimedia del proyecto

| Archivo | Tipo | Origen | Licencia |
|---|---|---|---|
| `public/imagenes/perfil.jpg` | Fotografía de perfil | Producción propia | Propia |
| `public/audio/presentacion.mp3` | Audio de autopresentación | Grabación propia, editada en Audacity | Propia |
| `public/video/intro.mp4` | Video de introducción | Producción propia | Propia |

---

## 4. Herramientas 

| Herramienta | Uso |
|---|---|
| ffmpeg | Comprimir el video (85 MB → 9.7 MB) y convertir el audio a MP3 |
| CapCut | Edición del video de introducción personal |
| Adobe Podcast Enhance (podcast.adobe.com) | Mejorar la calidad del audio de autopresentación con IA (eliminación de ruido) y agregar música de dondo |

---

## 5. Uso de Inteligencia Artificial

Se utilizó **Claude (Anthropic)** como asistente durante el desarrollo del proyecto para:

- Generar y refinar código de componentes Vue 3 (`Header.vue`, `Gallery.vue`, `Skills.vue`, etc.)
- Corregir errores y aplicar buenas prácticas de CSS moderno (variables, media queries con rangos, `rgb()` con alpha)
- Revisar el código contra las convenciones del curso (semántica HTML, módulos ESM)
- Convertir y comprimir archivos multimedia con ffmpeg
- Redactar y estructurar este `REFERENCIAS.md` y el `README.md`

Todo el código generado fue revisado, comprendido y adaptado al contexto específico del proyecto.

---