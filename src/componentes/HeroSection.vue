<script setup>
defineProps({
  nombre: String,
  titulo: String,
  universidad: String,
  video: String,   // "/video/intro.mp4"
})

// Controla si el modal del video está abierto o cerrado
import { ref } from 'vue'
const videoAbierto = ref(false)

function abrirVideo() {
  videoAbierto.value = true
}

function cerrarVideo() {
  videoAbierto.value = false
}
</script>

<template>
  <section class="hero">

    <!-- CONTENIDO PRINCIPAL -->
    <div class="hero-contenido">

      <p class="badge">Estudiante · UCR · Costa Rica</p>

      <h1>
        <span class="nombre-top">{{ nombre.split(' ').slice(0, 2).join(' ') }}</span>
        <span class="nombre-bottom">{{ nombre.split(' ').slice(2).join(' ') }}</span>
      </h1>

      <p class="subtitulo">{{ titulo }} — {{ universidad }}</p>

      <!-- BOTONES -->
      <div class="botones">

        <a href="#contacto" class="btn btn-primario">
          Contacto
        </a>

        <!-- Al hacer clic llama a abrirVideo() que cambia videoAbierto a true -->
        <button class="btn btn-secundario" @click="abrirVideo">
          Ver video de introducción
        </button>

      </div>
    </div>

    <!-- DECORACIÓN DE FONDO -->
    <div class="deco" aria-hidden="true">
      <div class="anillo a1"></div>
      <div class="anillo a2"></div>
      <div class="cuadricula"></div>
    </div>

  </section>

  <!-- MODAL DEL VIDEO -->
  <!-- v-if muestra el modal solo cuando videoAbierto es true -->
  <div v-if="videoAbierto" class="modal-fondo" @click="cerrarVideo">

    <!--
      @click.stop evita que el clic en el video cierre el modal
      (sin esto, cualquier clic adentro también cerraría el modal)
    -->
    <div class="modal-contenido" @click.stop>

      <button class="modal-cerrar" @click="cerrarVideo">✕</button>

      <video controls autoplay :src="video" class="video-player">
        Tu navegador no soporta video.
      </video>

    </div>
  </div>
</template>

<style scoped>
/* ── HERO ── */
.hero {
  min-height: 92vh;
  display: flex;
  align-items: center;
  padding: 0 2.5rem;
  position: relative;
  overflow: hidden;
  border-bottom: 1px solid #1e2030;
}

.hero-contenido {
  position: relative;
  z-index: 2;
  max-width: 640px;
}

/* Badge superior */
.badge {
  font-size: 0.72rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: #4f7fff;
  margin-bottom: 1.5rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.badge::before {
  content: '';
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: #3ecf8e;   /* punto verde */
  display: inline-block;
  animation: parpadeo 2s infinite;
}

@keyframes parpadeo {
  0%, 100% { opacity: 1; }
  50%       { opacity: 0.2; }
}

/* Nombre grande */
h1 {
  font-size: clamp(3rem, 8vw, 6rem);
  font-weight: 800;
  line-height: 0.95;
  letter-spacing: -0.03em;
  margin-bottom: 1.25rem;
}

.nombre-top {
  display: block;
  color: #ffffff;
}

.nombre-bottom {
  display: block;
  color: #4f7fff;   /* apellidos en azul */
}

.subtitulo {
  font-size: 0.95rem;
  color: #6b738a;
  margin-bottom: 2.5rem;
}

/* Botones */
.botones {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
}

.btn {
  font-size: 0.82rem;
  font-weight: 500;
  padding: 0.7rem 1.5rem;
  border-radius: 4px;
  text-decoration: none;
  cursor: pointer;
  border: none;
  transition: all 0.2s;
  font-family: inherit;
}

.btn-primario {
  background: #4f7fff;
  color: #ffffff;
}

.btn-primario:hover {
  background: #6b93ff;
}

.btn-secundario {
  background: transparent;
  color: #c8cedf;
  border: 1px solid #2a2a3a;
}

.btn-secundario:hover {
  border-color: #4f7fff;
  color: #4f7fff;
}

/* ── MODAL ── */
.modal-fondo {
  /* cubre toda la pantalla por encima de todo */
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.85);
  z-index: 999;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1.5rem;
}

.modal-contenido {
  position: relative;
  width: 100%;
  max-width: 780px;
  background: #0f1219;
  border: 1px solid #2a2a3a;
  border-radius: 8px;
  overflow: hidden;
}

.modal-cerrar {
  position: absolute;
  top: 0.75rem;
  right: 0.75rem;
  z-index: 10;
  background: rgba(0,0,0,0.6);
  color: #ffffff;
  border: none;
  border-radius: 50%;
  width: 32px;
  height: 32px;
  font-size: 0.85rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.2s;
}

.modal-cerrar:hover {
  background: #4f7fff;
}

.video-player {
  width: 100%;
  display: block;
  max-height: 70vh;
  background: #000;
}
</style>