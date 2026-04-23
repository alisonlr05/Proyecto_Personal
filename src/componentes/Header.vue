<script setup>
// Recibe los datos del perfil desde App.vue
defineProps({
  nombre: String,
})
</script>

<template>
  <header>
    <div class="header-texto">
      <h1>{{ nombre }}</h1>
    </div>

    <nav>
      <a href="#about">Sobre mí</a>
      <a href="#skills">Skills</a>
      <a href="#galeria">Proyectos</a>
      <a href="#contacto">Contacto</a>
    </nav>
  </header>
</template>

<style scoped>
header {
  background-color: #0A0908;
  padding: 1.5rem 3rem;
  border-bottom: 1px solid #2a2a3a;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}

h1 {
  font-size: 1.4rem;
  color: #F2F4F3;
  margin-bottom: 0.2rem;
}


nav {
  display: flex;
  gap: 2.15rem;
}

nav a {
  color: #A9927D;
  text-decoration: none;
  font-size: 0.875rem;
}

nav a:hover {
  color: #4f7fff;
}
</style>