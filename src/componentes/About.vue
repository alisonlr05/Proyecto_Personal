<script setup>
import { ref } from 'vue'
import { Headphones, Video } from 'lucide-vue-next'

defineProps({
  descripcion: String,
  foto: String,
  audio: String,
  video: String,
})

const audioReproduciendo = ref(false)
const videoReproduciendo = ref(false)
</script>

<template>
  <section id="sobre-mi" class="about">
    <h2 class="about__titulo">Sobre Mí</h2>
    <div class="about__linea"></div>

    <div class="about__grid">

      <!-- FOTO -->
      <div class="about__foto-wrap">
        <img :src="foto" alt="Foto de perfil de Alison López"
     class="about__foto" loading="lazy" decoding="async" />
      </div>

      <div class="about__contenido">

        <!-- DESCRIPCIÓN -->
        <div class="about__descripcion">
  <p
    v-for="(parrafo, i) in descripcion.split('|')"
    :key="i"
  >{{ parrafo }}</p>
</div>

        <!-- AUDIO -->
        <div class="about__media-label">
          <Headphones :size="21" :class="{ 'icono--bailando': audioReproduciendo }" />
          <span>Audio de presentación</span>
        </div>
        <audio controls :src="audio" class="about__audio" @play="audioReproduciendo = true"
          @pause="audioReproduciendo = false" @ended="audioReproduciendo = false">
          Tu navegador no soporta audio.
        </audio>

        <!-- VIDEO -->
        <div class="about__media-label">
          <Video :size="23" :class="{ 'icono--bailando': videoReproduciendo }" />
          <span>Video de presentación</span>
        </div>
        <video controls preload="metadata" class="about__video"
          @play="videoReproduciendo = true"
          @pause="videoReproduciendo = false"
          @ended="videoReproduciendo = false">
          <source :src="video.replace('.mp4', '.webm')" type="video/webm" />
          <source :src="video" type="video/mp4" />
          Tu navegador no soporta video.
        </video>
      
      </div>

    </div>
  </section>
</template>

<style scoped>
.about {
  padding: 5rem 4rem;
}

.about__titulo {
  font-family: 'Playfair Display', serif;
  font-size: 2.2rem;
  color: #471010;
  font-weight: 700;
  text-align: center;
  margin-bottom: 0.5rem;
}

.about__linea {
  width: 60px;
  height: 2px;
  background-color: #6c533d;
  margin: 0 auto 3rem;
}

.about__grid {
  display: flex;
  gap: 3rem;
  align-items: flex-start;
  max-width: 900px;
  margin: 0 auto;
}

/* FOTO */
.about__foto-wrap {
  flex-shrink: 0;
  width: 270px;
  height: 270px;
  border-radius: 50%;
  border: 3px dashed #a1b5a1;
  padding: 6px;
}

.about__foto {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  object-fit: cover;
  object-position: center 40%;
  background-color: #e8e2dc;
}

/* CONTENIDO */
.about__descripcion p {
  font-size: 1rem;
  line-height: 1.8;
  margin-bottom: 1.5rem;
}

.about__descripcion {
  color: #471010;
  font-size: 1rem;
  line-height: 1.8;
}

.about__media-label {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.78rem;
  font-weight: 600;
  color: #6c533d;
  letter-spacing: 0.04em;
  text-transform: uppercase;
}

.about__audio {
  width: 100%;
  accent-color: #6c533d;
}

.about__video {
  width: 100%;
  border-radius: 10px;
  background-color: #1a1a1a;
}

/* Modo oscuro */
body.tema-oscuro .about__titulo {
  color: #e8e0d8;
}

body.tema-oscuro .about__linea {
  background-color: #496f49;
}

body.tema-oscuro .about__foto-wrap {
  border-color: #7a9e7a;
}

body.tema-oscuro .about__foto {
  background-color: #2a2420;
}

body.tema-oscuro .about__descripcion {
  color: #e8e0d8;
}

body.tema-oscuro .about__media-label {
  color: #a1856a;
}

body.tema-oscuro .about__audio {
  accent-color: #a1856a;
}

/* MÓVIL */
@media (max-width: 768px) {
  .about { padding: 4rem 1.5rem; }

  .about__grid {
    flex-direction: column;
    align-items: center;
  }
}

/* animacion para iconos */
.icono--bailando {
  animation: saltar 0.5s ease-in-out infinite alternate;
}

@keyframes saltar {
  0%   { transform: translateY(0px);  }
  100% { transform: translateY(-4px); }
}
</style>