<script setup>
import { ref, onMounted, watch } from 'vue'
import Header    from './componentes/Header.vue'
import HeroSection from './componentes/HeroSection.vue'
import About     from './componentes/About.vue'
import Skills    from './componentes/Skills.vue'
import Proyectos from './componentes/Gallery.vue'
import Contacto  from './componentes/Contacto.vue'

const datos      = ref(null)
const cargando   = ref(true)
const temaOscuro = ref(false)

onMounted(async () => {
  const respuesta = await fetch('/data/datos.json')
  datos.value     = await respuesta.json()
  cargando.value  = false
})

watch(temaOscuro, (oscuro) => {
  document.body.classList.toggle('tema-oscuro', oscuro)
})

function toggleTema() {
  temaOscuro.value = !temaOscuro.value
}
</script>

<template>
  <p v-if="cargando">Cargando...</p>

  <div v-else-if="datos">
    <Header
      :nombre="datos.perfil.nombreCompleto"
      :temaOscuro="temaOscuro"
      @toggleTema="toggleTema"
    />

    <main>
      <HeroSection
        :nombre="datos.perfil.nombreCompleto"
        :titulo="datos.perfil.titulo"
        :universidad="datos.perfil.universidad"
      />

      <About
        :descripcion="datos.perfil.descripcion"
        :foto="datos.perfil.foto"
        :audio="datos.perfil.audio"
        :video="datos.perfil.video"
      />

      <Skills :habilidades="datos.habilidades" />

      <Proyectos :proyectos="datos.proyectos" />

      <Contacto :contacto="datos.contacto" />
    </main>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@300;400;500&family=Jost:ital,wght@0,100..900;1,100..900&family=Playfair+Display:ital,wght@0,400..900;1,400..900&display=swap');

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
  font-family: 'DM Sans', sans-serif;
  background-color: #f8f5f2;
  color: #471010;
  transition: background-color 0.3s ease, color 0.3s ease;
}

body.tema-oscuro {
  background-color: #1a1612;
  color: #e8e0d8;
}

.particula {
  position: absolute;
  width: 7px;
  height: 7px;
  border-radius: 75%;
  background-color: #534132;
  pointer-events: none;
  transform: translate(-50%, -50%);
  animation: explotar 0.7s ease-out forwards;
}

body.tema-oscuro .particula {
  background-color: #c4ccc4;
}

@keyframes explotar {
  0% {
    transform: translate(-50%, -50%) rotate(var(--angulo)) translateX(0px);
    opacity: 1;
  }
  100% {
    transform: translate(-50%, -50%) rotate(var(--angulo)) translateX(var(--distancia));
    opacity: 0;
  }
}
</style>