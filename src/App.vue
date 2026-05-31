<script setup>
import { ref, onMounted } from 'vue'
import Header from './componentes/Header.vue'
import HeroSection from './componentes/HeroSection.vue'
import About  from './componentes/About.vue'
import Skills from './componentes/Skills.vue'

const datos    = ref(null)
const cargando = ref(true)

onMounted(async () => {
  const respuesta = await fetch('/data/datos.json')
  datos.value     = await respuesta.json()
  cargando.value  = false
})
</script>

<template>
  <p v-if="cargando">Cargando...</p>

  <div v-else-if="datos">

    <!-- datos.perfil es el objeto "perfil" del JSON -->
    <Header
      :nombre="datos.perfil.nombreCompleto"
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
    </main>

  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@300;400;500&display=swap');

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html  { scroll-behavior: smooth; }

body  {
  font-family: 'DM Sans', sans-serif;
  background-color: #0A0908;
  color: #c8cedf;
}
</style>