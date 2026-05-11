<script setup>
defineProps({
  descripcion: String,
  foto:        String,
  audio:       String,
  video:       String,
})
</script>

<template>
  <section id="sobre-mi" class="about">
    <h2 class="about__titulo">Sobre Mí</h2>
    <div class="about__linea"></div>

    <div class="about__grid">

      <!-- FOTO -->
      <div class="about__foto-wrap">
        <img :src="foto" alt="Foto de perfil" class="about__foto" />
      </div>

      <div class="about__contenido">

        <!-- DESCRIPCIÓN -->
        <p class="about__descripcion">{{ descripcion }}</p>

        <!-- AUDIO -->
        <p class="about__media-label">🎧 Audio de presentación</p>
        <audio controls :src="audio" class="about__audio">
          Tu navegador no soporta audio.
        </audio>

        <!-- VIDEO -->
        <p class="about__media-label">🎬 Video de presentación</p>
        <video controls :src="video" class="about__video">
          Tu navegador no soporta video.
        </video>

      </div>
    </div>
  </section>
</template>

<style scoped>
.about {
  background-color: #f8f5f2;
  padding: 5rem 4rem;
}

.about__titulo {
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
  width: 200px;
  height: 200px;
  border-radius: 50%;
  border: 2px dashed #a1b5a1;
  padding: 6px;
}

.about__foto {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  object-fit: cover;
  background-color: #e8e2dc;
}

/* CONTENIDO */
.about__contenido {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.about__descripcion {
  color: #471010;
  font-size: 1rem;
  line-height: 1.8;
}

.about__media-label {
  font-size: 0.9rem;
  color: #6c533d;
  font-weight: 500;
  margin-bottom: 0.2rem;
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

/* MÓVIL */
@media (max-width: 768px) {
  .about { padding: 4rem 1.5rem; }

  .about__grid {
    flex-direction: column;
    align-items: center;
  }
}
</style>