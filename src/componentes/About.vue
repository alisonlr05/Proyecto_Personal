<script setup>
// Recibe los datos del perfil desde App.vue
defineProps({
  descripcion: String,
  foto: String,   // "/images/perfil.jpg"
  audio: String,  // "/audio/presentacion.mp3"
})
</script>

<template>
  <section id="about">
    <h2>Sobre mí</h2>

    <div class="about-grid">

      <!-- FOTO -->
      <!-- :src usa el valor de la prop "foto", no el texto literal "foto" -->
      <img :src="foto" alt="Foto de perfil" class="foto" />

      <div class="about-texto">
        <p>{{ descripcion }}</p>

        <!-- AUDIO -->
        <!-- "controls" le dice al navegador que muestre play/pausa/volumen -->
        <!-- :src usa el valor de la prop "audio" -->
        <div class="audio-wrap">
          <p class="audio-label">Autopresentación:</p>
          <audio controls :src="audio">
            Tu navegador no soporta audio.
          </audio>
        </div>

      </div>
    </div>
  </section>
</template>

<style scoped>
section {
  padding: 3rem 2rem;
  border-bottom: 1px solid #1e2030;
  max-width: 800px;
  margin: 0 auto;
}

h2 {
  font-size: 1.3rem;
  color: #ffffff;
  margin-bottom: 1.5rem;
}

.about-grid {
  display: flex;
  gap: 2rem;
  align-items: flex-start;
  flex-wrap: wrap;  /* en móvil se apilan verticalmente */
}

.foto {
  width: 150px;
  height: 180px;
  object-fit: cover;   /* recorta la imagen para que llene el espacio */
  border-radius: 6px;
  border: 1px solid #2a2a3a;
  flex-shrink: 0;      /* evita que se achique */
}

.about-texto {
  flex: 1;
  min-width: 220px;
}

p {
  color: #c8cedf;
  line-height: 1.8;
  font-size: 0.95rem;
  margin-bottom: 1.5rem;
}

.audio-label {
  font-size: 0.78rem;
  color: #6b738a;
  margin-bottom: 0.4rem;
}

audio {
  width: 100%;
  accent-color: #4f7fff;  /* colorea los controles del reproductor */
}
</style>