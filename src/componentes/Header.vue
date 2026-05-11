<script setup>
defineProps({
  nombre: String,
})
</script>

<template>
  <header class="header">
    <div class="header__logo">
      <span class="header__icono">✦</span>
      <span>Portfolio</span>
    </div>

    <nav class="header__nav">
      <a href="#inicio">Inicio</a>
      <a href="#sobre-mi">Sobre Mí</a>
      <a href="#skills">Skills</a>
      <a href="#proyectos">Proyectos</a>
      <a href="#contacto">Contacto</a>
    </nav>
  </header>
</template>

<style scoped>
.header {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1.2rem 4rem;
  background-color: #f8f5f2;
  border-bottom: 1px solid rgba(71, 16, 16, 0.08);
}

.header__logo {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-weight: 600;
  color: #471010;
  font-size: 1rem;
  letter-spacing: 0.02em;
}

.header__icono {
  color: #6c533d;
  font-size: 1rem;
}

.header__nav {
  display: flex;
  gap: 2.5rem;
}

.header__nav a {
  text-decoration: none;
  color: #471010;
  font-size: 0.9rem;
  font-weight: 400;
  letter-spacing: 0.01em;
  position: relative;
  transition: color 0.2s;
}

.header__nav a::after {
  content: '';
  position: absolute;
  bottom: -3px;
  left: 0;
  width: 0;
  height: 1px;
  background-color: #6c533d;
  transition: width 0.25s;
}

.header__nav a:hover {
  color: #6c533d;
}

.header__nav a:hover::after {
  width: 100%;
}
</style>