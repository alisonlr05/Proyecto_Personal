<script setup>
defineProps({
  habilidades: Array,
})

const iconos = {
  'Java': `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
    <path d="M8.5 20.5s-1.5.9 1.1.6c3.1-.4 4.7-.3 8.1.3 0 0 .9.6.2.8-3.3 1.1-13.6.7-11-1.7zm-.9-2.8s-1.7 1.3 1 1.1c3.5-.3 6.3-.3 8.9.1 0 0 .6.7-.1.8-3.5.7-11.9.2-9.8-2zm5.1-8.9c1.6 1.9.4 3.5.4 3.5s3.9-2 2.1-4.5c-1.7-2.3-3-3.5 4-7.5 0 0-11 2.8-6.5 8.5z"/>
    <path d="M15.5 19.5s1.1.9-1.2 1.6c-4.5 1.4-18.5.5-15-1.5.5-.3 1.5-.6 1.5-.6s-2.4 1.6 14.7.5z"/>
  </svg>`,

  'PHP': `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
    <ellipse cx="12" cy="12" rx="10" ry="6"/>
    <path d="M9 14V10h2.5a1.5 1.5 0 0 1 0 3H9"/>
    <path d="M14 14l1-4h2a1 1 0 0 1 .9 1.4L17 13h-2l-.5 1H14z"/>
  </svg>`,

  'C#': `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
    <path d="M9.5 8.5A4 4 0 1 0 9.5 15.5"/>
    <line x1="15" y1="9" x2="15" y2="15"/>
    <line x1="18" y1="9" x2="18" y2="15"/>
    <line x1="13.5" y1="11" x2="19.5" y2="11"/>
    <line x1="13.5" y1="13" x2="19.5" y2="13"/>
  </svg>`,

  'JavaScript': `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
    <rect x="3" y="3" width="18" height="18" rx="2"/>
    <path d="M8 17c0 1.5 2.5 2 3 0V12"/>
    <path d="M13 12h4M15 12v5"/>
  </svg>`,

  'HTML5': `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
    <path d="M4 3l1.5 17L12 22l6.5-2L20 3H4z"/>
    <path d="M16 8H8l.5 4.5h7l-.5 5-3 1-3-1-.2-2.5"/>
  </svg>`,

  'CSS3': `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
    <path d="M4 3l1.5 17L12 22l6.5-2L20 3H4z"/>
    <path d="M16.5 8h-9l.4 4h8.2l-.6 5.5-3.5 1-3.5-1-.2-2.5"/>
  </svg>`,

  'Vue.js': `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
    <path d="M2 4l10 16L22 4h-4l-6 10L8 4H2z"/>
    <path d="M6 4l6 10 6-10h-3l-3 5-3-5H6z"/>
  </svg>`,

  'Node.js': `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
    <path d="M12 2L3 7v10l9 5 9-5V7L12 2z"/>
    <path d="M12 2v20M3 7l9 5 9-5"/>
  </svg>`,

  'Laravel': `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
    <path d="M21 8l-9-6-9 6v8l9 6 9-6V8z"/>
    <path d="M3 8l9 6 9-6"/>
    <path d="M12 14v8"/>
  </svg>`,

  'ASP.NET': `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
    <circle cx="12" cy="12" r="9"/>
    <path d="M3 12h18"/>
    <path d="M12 3a15 15 0 0 1 0 18"/>
    <path d="M12 3a15 15 0 0 0 0 18"/>
  </svg>`,

  'MySQL': `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
    <ellipse cx="12" cy="5" rx="9" ry="3"/>
    <path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"/>
    <path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"/>
  </svg>`,

  'SQLite': `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
    <ellipse cx="12" cy="6" rx="7" ry="3"/>
    <path d="M19 6v6c0 1.66-3.13 3-7 3s-7-1.34-7-3V6"/>
    <path d="M5 12v6c0 1.66 3.13 3 7 3"/>
    <path d="M19 12c0 1.66-3.13 3-7 3"/>
    <path d="M16 18l2 2 4-4"/>
  </svg>`,

  'Git': `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
    <circle cx="6" cy="6" r="2"/>
    <circle cx="18" cy="6" r="2"/>
    <circle cx="6" cy="18" r="2"/>
    <path d="M8 6h8M6 8v8"/>
    <path d="M16 8v3a3 3 0 0 1-3 3H9"/>
  </svg>`,

  'GitHub': `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
    <path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"/>
  </svg>`,

  'Docker': `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
    <path d="M22 12.5c0 .28-.02.55-.06.82A5 5 0 0 1 17 18H5a3 3 0 0 1-.6-5.93A6 6 0 0 1 16 7h1a5 5 0 0 1 5 5.5z"/>
    <path d="M7 13h2v-2H7zm3 0h2v-2h-2zm3 0h2v-2h-2zm-3-3h2V8h-2zm3 0h2V8h-2z"/>
  </svg>`,

  'Máquinas Virtuales': `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
    <rect x="2" y="3" width="20" height="14" rx="2"/>
    <path d="M8 21h8M12 17v4"/>
    <rect x="6" y="7" width="5" height="4" rx="1"/>
    <rect x="13" y="7" width="5" height="4" rx="1"/>
  </svg>`,

  'Redes': `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
    <circle cx="12" cy="5" r="2"/>
    <circle cx="5" cy="19" r="2"/>
    <circle cx="19" cy="19" r="2"/>
    <path d="M12 7v4M12 11l-5 6M12 11l5 6"/>
  </svg>`,
}
</script>

<template>
  <section id="skills" class="skills">
    <h2 class="skills__titulo">Skills</h2>
    <div class="skills__linea"></div>

    <div class="skills__grid">
      <div
        v-for="skill in habilidades"
        :key="skill.nombre"
        class="skill-card"
      >
        <!-- Marco SVG animado -->
        <svg class="skill-card__frame" viewBox="0 0 180 120" preserveAspectRatio="none">
          <path class="frame-path" d="M 10,10 H 170 V 110 H 10 Z" />
        </svg>

        <p class="skill-card__categoria">{{ skill.categoria }}</p>
        <h3 class="skill-card__nombre">{{ skill.nombre }}</h3>

        <!-- Ícono -->
        <div class="skill-card__icono" v-html="iconos[skill.nombre]"></div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.skills {
  padding: 5rem 4rem;
  text-align: center;
}

.skills__titulo {
  font-family: 'Playfair Display', serif;
  font-size: 2.2rem;
  color: #471010;
  font-weight: 700;
  margin-bottom: 0.5rem;
}

.skills__linea {
  width: 60px;
  height: 2px;
  background-color: #6c533d;
  margin: 0 auto 3rem;
}

.skills__grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1.5rem;
  max-width: 900px;
  margin: 0 auto;
}

.skill-card {
  position: relative;
  background-color: #ffffff;
  border: 1px solid rgba(71, 16, 16, 0.1);
  border-radius: 12px;
  padding: 1.8rem 2rem;
  width: 180px;
  text-align: center;
  cursor: default;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
}

.skill-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 28px rgba(71, 16, 16, 0.12);
}

/* Marco SVG */
.skill-card__frame {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  border-radius: 12px;
}

.frame-path {
  fill: none;
  stroke: #6c533d;
  stroke-width: 1.5;
  stroke-dasharray: 520;
  stroke-dashoffset: 520;
  transition: stroke-dashoffset 0.8s cubic-bezier(0.16, 1, 0.3, 1);
}

.skill-card:hover .frame-path {
  stroke-dashoffset: 0;
}

.skill-card__categoria {
  font-size: 0.72rem;
  color: #3e523e;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  margin-bottom: 0.8rem;
}

.skill-card__nombre {
  font-family: 'Jost', sans-serif;
  font-size: 1.1rem;
  color: #471010;
  font-weight: 600;
  margin-bottom: 0.8rem;
}

.skill-card__icono {
  width: 32px;
  height: 32px;
  margin: 0 auto;
  color: #6c533d;
  transition: color 0.3s ease;
}

.skill-card__icono svg {
  width: 100%;
  height: 100%;
}

/* Modo oscuro */
body.tema-oscuro .skills__titulo {
  color: #e8e0d8;
}

body.tema-oscuro .skills__linea {
  background-color: #496f49;
}

body.tema-oscuro .skill-card {
  background-color: #2a2420;
  border-color: rgba(232, 224, 216, 0.1);
}

body.tema-oscuro .skill-card:hover {
  box-shadow: 0 12px 28px rgba(0, 0, 0, 0.3);
}

body.tema-oscuro .frame-path {
  stroke: #a1856a;
}

body.tema-oscuro .skill-card__categoria {
  color: #7a9e7a;
}

body.tema-oscuro .skill-card__nombre {
  color: #e8e0d8;
}

body.tema-oscuro .skill-card__icono {
  color: #a1856a;
}
</style>