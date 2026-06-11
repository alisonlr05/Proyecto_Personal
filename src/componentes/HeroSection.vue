<script setup>
import { Cpu } from 'lucide-vue-next'

defineProps({
  nombre:      String,
  titulo:      String,
  universidad: String,
})

function lanzarParticulas(evento) {
  const boton = evento.currentTarget
  const rect  = boton.getBoundingClientRect()

  for (let i = 0; i < 8; i++) {
    const particula = document.createElement('span')
    particula.classList.add('particula')

    const angulo    = (i / 8) * 360
    const distancia = 60 + Math.random() * 40

    particula.style.setProperty('--angulo',    `${angulo}deg`)
    particula.style.setProperty('--distancia', `${distancia}px`)
    particula.style.left = `${rect.width  / 2}px`
    particula.style.top  = `${rect.height / 2}px`

    boton.appendChild(particula)
    setTimeout(() => particula.remove(), 600)
  }
}
</script>

<template>
  <section class="hero" id="inicio">

    <div class="hero__deco">
      <!-- HTML5 -->
      <div class="deco deco--1">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
          <path d="M4 3l1.5 17L12 22l6.5-2L20 3H4z"/>
          <path d="M16 8H8l.5 4.5h7l-.5 5-3 1-3-1-.2-2.5"/>
        </svg>
      </div>

      <!-- CSS3 -->
      <div class="deco deco--2">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
          <path d="M4 3l1.5 17L12 22l6.5-2L20 3H4z"/>
          <path d="M16.5 8h-9l.4 4h8.2l-.6 5.5-3.5 1-3.5-1-.2-2.5"/>
        </svg>
      </div>

      <!-- JavaScript -->
      <div class="deco deco--3">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
          <rect x="3" y="3" width="18" height="18" rx="2"/>
          <path d="M8 17c0 1.5 2.5 2 3 0V12"/>
          <path d="M13 12h4M15 12v5"/>
        </svg>
      </div>

      <!-- Vue -->
      <div class="deco deco--4">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
          <path d="M2 4l10 16L22 4h-4l-6 10L8 4H2z"/>
          <path d="M6 4l6 10 6-10h-3l-3 5-3-5H6z"/>
        </svg>
      </div>

      <!-- GitHub -->
      <div class="deco deco--5">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
          <path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"/>
        </svg>
      </div>

      <!-- Base de datos -->
      <div class="deco deco--6">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
          <ellipse cx="12" cy="5" rx="9" ry="3"/>
          <path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"/>
          <path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"/>
        </svg>
      </div>

      <!-- Nube -->
      <div class="deco deco--7">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
          <path d="M18 10h-1.26A8 8 0 1 0 9 20h9a5 5 0 0 0 0-10z"/>
        </svg>
      </div>
   </div>

   <!-- Cpu -->
    <div class="deco deco--cpu">
      <Cpu :size="36" />
    </div>

    <div class="hero__contenido">
      <p class="hero__saludo">¡Hola! Soy</p>
      <h1 class="hero__nombre">{{ nombre }}</h1>
      <h2 class="hero__titulo">{{ titulo }}</h2>
      <p class="hero__universidad">{{ universidad }}</p>

      <!-- BOTONES -->
      <div class="hero__botones">
        <a href="#contacto" class="btn btn--solido" @mouseenter="lanzarParticulas">Contacto</a>
        <a href="#proyectos" class="btn btn--borde" @mouseenter="lanzarParticulas">Ver Proyectos</a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 8rem 2rem 4rem;
  text-align: center;
  overflow: hidden;
}

/* Íconos decorativos */
.hero__deco {
  position: absolute;
  inset: 0;
  pointer-events: none;
}

.deco {
  position: absolute;
  opacity: 0.18;
  color: #37291d;
  transition: color 0.3s ease, opacity 0.3s ease;
}

body.tema-oscuro .deco {
  color: #a1b5a1;
  opacity: 0.25;
}

.deco svg { width: 100%; height: 100%; }

.deco--1 { width: 48px; height: 48px; top: 12%;  left: 8%;   animation: flotar1 6s ease-in-out infinite; }
.deco--2 { width: 38px; height: 38px; top: 70%;  left: 5%;   animation: flotar2 7s ease-in-out infinite; }
.deco--3 { width: 44px; height: 44px; top: 20%;  right: 7%;  animation: flotar3 5s ease-in-out infinite; }
.deco--4 { width: 52px; height: 52px; top: 65%;  right: 6%;  animation: flotar1 8s ease-in-out infinite; }
.deco--5 { width: 40px; height: 40px; top: 80%;  left: 20%;  animation: flotar2 6s ease-in-out infinite; }
.deco--6 { width: 36px; height: 36px; top: 15%;  right: 22%; animation: flotar3 7s ease-in-out infinite; }
.deco--7 { width: 56px; height: 56px; top: 78%;  right: 18%; animation: flotar1 9s ease-in-out infinite; }

@keyframes flotar1 {
  0%, 100% { transform: translateY(0px);   }
  50%       { transform: translateY(-12px); }
}
@keyframes flotar2 {
  0%, 100% { transform: translateY(0px)  rotate(0deg);  }
  50%       { transform: translateY(-8px) rotate(5deg);  }
}
@keyframes flotar3 {
  0%, 100% { transform: translateY(0px)   rotate(0deg);  }
  50%       { transform: translateY(-10px) rotate(-5deg); }
}

/* Contenido */
.hero__contenido {
  position: relative;
  z-index: 1;
  max-width: 680px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.4rem;
}

.hero__saludo {
  color: #365436;
  font-size: 1rem;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  margin-bottom: 0.2rem;
  transition: color 0.3s ease;
}

body.tema-oscuro .hero__saludo {
  color: #7aaa7a;
}

.hero__nombre {
  font-family: 'Playfair Display', serif;
  font-size: clamp(2.8rem, 9vw, 5.5rem);
  color: #471010;
  font-weight: 700;
  line-height: 1.05;
  margin: 0;
  transition: color 0.3s ease;
}

body.tema-oscuro .hero__nombre {
  color: #e1d4d4;
}

.hero__titulo {
  font-size: clamp(1rem, 2.5vw, 1.4rem);
  color: #6c533d;
  font-weight: 400;
  font-style: italic;
  padding-bottom: 0.3rem;
  border-bottom: 2px solid #a1b5a1;
  margin-top: 0.4rem;
  transition: color 0.3s ease, border-color 0.3s ease;
}

body.tema-oscuro .hero__titulo {
  color: #c4a882;
  border-bottom-color: #7a9e7a;
}

.hero__universidad {
  color: #7d545a;
  font-size: 0.9rem;
  margin-top: 0.2rem;
  margin-bottom: 1.5rem;
  transition: color 0.3s ease;
}

body.tema-oscuro .hero__universidad {
  color: #c49aa0;
}

.hero__botones {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  justify-content: center;
  margin-top: 1rem;
}

.btn {
  padding: 0.75rem 2rem;
  border-radius: 999px;
  font-size: 0.95rem;
  font-weight: 500;
  text-decoration: none;
  transition: all 0.25s ease;
  cursor: pointer;
  position: relative;
  overflow: visible;
}

.btn--solido {
  background-color: #471010;
  color: #f8f5f2;
  border: 2px solid #471010;
}
.btn--solido:hover {
  background-color: #6c533d;
  border-color: #6c533d;
}

body.tema-oscuro .btn--solido {
  background-color: #a1856a;
  border-color: #a1856a;
  color: #1a1612;
}

body.tema-oscuro .btn--solido:hover {
  background-color: #c4a882;
  border-color: #c4a882;
}

.btn--borde {
  background-color: transparent;
  color: #471010;
  border: 2px solid #471010;
}
.btn--borde:hover {
  background-color: #471010;
  color: #f8f5f2;
}

body.tema-oscuro .btn--borde {
  color: #e8e0d8;
  border-color: #e8e0d8;
}
body.tema-oscuro .btn--borde:hover {
  background-color: #e8e0d8;
  color: #1a1612;
}

.deco--cpu {
  position: absolute;
  left: 15%;
  top: 45%;
  opacity: 0.15;
  color: #37291d;
  animation: flotar2 7s ease-in-out infinite;
  transition: color 0.3s ease, opacity 0.3s ease;
}

body.tema-oscuro .deco--cpu {
  color: #a1b5a1;
  opacity: 0.25;
}

@media (max-width: 480px) {
  .hero__botones { flex-direction: column; width: 100%; }
  .btn { text-align: center; }
}
</style>