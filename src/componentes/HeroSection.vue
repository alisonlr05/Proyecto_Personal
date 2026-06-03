<script setup>
defineProps({
  nombre:      String,
  titulo:      String,
  universidad: String,
})
</script>

<template>
  <section class="hero" id="inicio">
    <div class="hero__contenido">
      <p class="hero__saludo">¡Hola! Soy</p>
      <h1 class="hero__nombre">{{ nombre }}</h1>
      <h2 class="hero__titulo">{{ titulo }}</h2>
      <p class="hero__universidad">{{ universidad }}</p>

      <div class="hero__botones">
        <a href="#contacto"  class="btn btn--solido">Contacto</a>
        <a href="#proyectos" class="btn btn--borde">Ver Proyectos</a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 8rem 2rem 4rem;
  text-align: center;
}

.hero__contenido {
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
}

.hero__nombre {
  font-size: clamp(2.8rem, 9vw, 5.5rem);
  color: #471010;
  font-weight: 700;
  line-height: 1.05;
  margin: 0;
}

.hero__titulo {
  font-size: clamp(1rem, 2.5vw, 1.4rem);
  color: #6c533d;
  font-weight: 400;
  font-style: italic;
  padding-bottom: 0.3rem;
  border-bottom: 2px solid #a1b5a1;
  margin-top: 0.4rem;
}

.hero__universidad {
  color: #7d545a;
  font-size: 0.9rem;
  margin-top: 0.2rem;
  margin-bottom: 1.5rem;
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

.btn--borde {
  background-color: transparent;
  color: #471010;
  border: 2px solid #471010;
}
.btn--borde:hover {
  background-color: #471010;
  color: #f8f5f2;
}

@media (max-width: 480px) {
  .hero__botones { flex-direction: column; width: 100%; }
  .btn { text-align: center; }
}
</style>