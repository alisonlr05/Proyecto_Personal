<script setup>
import { ExternalLink, Github, Play } from 'lucide-vue-next'

defineProps({
  proyectos: Array,
})
</script>

<template>
  <section id="proyectos" class="proyectos">
    <h2 class="proyectos__titulo">Proyectos</h2>
    <div class="proyectos__linea"></div>

    <div class="proyectos__grid">
      <article
        v-for="proyecto in proyectos"
        :key="proyecto.nombre"
        class="card"
      >
        <!-- Imagen con overlay al hacer hover -->
        <div class="card__imagen-wrap">
          <img
            v-if="proyecto.imagen"
            :src="proyecto.imagen"
            :alt="`Captura del proyecto ${proyecto.nombre}`"
            class="card__imagen"
            loading="lazy"
            decoding="async"
          />
          <div v-else class="card__imagen-placeholder"></div>

          <!-- Botones sobre la imagen -->
          <div class="card__overlay">
            <a
              v-if="proyecto.despliegue"
              :href="proyecto.despliegue"
              target="_blank"
              rel="noopener noreferrer"
              class="card__btn-icono"
              aria-label="Ver despliegue"
            >
              <ExternalLink :size="18" />
            </a>
            <a
              v-if="proyecto.video"
              :href="proyecto.video"
              target="_blank"
              rel="noopener noreferrer"
              class="card__btn-icono"
              aria-label="Ver video del proyecto"
            >
              <Play :size="18" />
            </a>
            <a
              v-if="proyecto.repositorio"
              :href="proyecto.repositorio"
              target="_blank"
              rel="noopener noreferrer"
              class="card__btn-icono"
              aria-label="Ver repositorio en GitHub"
            >
              <Github :size="18" />
            </a>
          </div>
        </div>

        <!-- Info -->
        <div class="card__info">
          <h3 class="card__nombre">{{ proyecto.nombre }}</h3>
          <p class="card__descripcion">{{ proyecto.descripcion }}</p>

          <ul class="card__tags" aria-label="Tecnologías">
            <li
              v-for="tec in proyecto.tecnologias"
              :key="tec"
              class="card__tag"
            >{{ tec }}</li>
          </ul>
        </div>
      </article>
    </div>
  </section>
</template>

<style scoped>
.proyectos {
  padding: 5rem 4rem;
  text-align: center;
}

.proyectos__titulo {
  font-family: 'Playfair Display', serif;
  font-size: 2.2rem;
  color: #471010;
  font-weight: 700;
  margin-bottom: 0.5rem;
}

.proyectos__linea {
  width: 60px;
  height: 2px;
  background-color: #6c533d;
  margin: 0 auto 3rem;
}

.proyectos__grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 2rem;
  max-width: 1000px;
  margin: 0 auto;
}

/* Card */
.card {
  background-color: #ffffff;
  border: 1px solid rgb(71 16 16 / 0.08);
  border-radius: 16px;
  width: 450px;
  overflow: hidden;
  text-align: left;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  cursor: default;
}

.card:hover {
  transform: translateY(-8px);
  box-shadow: 0 16px 36px rgb(71 16 16 / 0.13);
}

/* Imagen */
.card__imagen-wrap {
  position: relative;
  width: 100%;
  height: 190px;
  overflow: hidden;
}

.card__imagen {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  filter: sepia(0.45) saturate(0.8) hue-rotate(330deg) brightness(0.88);
  transition: filter 0.3s ease, transform 0.3s ease;
}

.card:hover .card__imagen {
  transform: scale(1.04);
}

.card__imagen-placeholder {
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, #6c533d, #a1b5a1);
}

/* Overlay con botones */
.card__overlay {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
  background-color: rgb(71 16 16 / 0.45);
  opacity: 0;
  transition: opacity 0.25s ease;
}

.card:hover .card__overlay {
  opacity: 1;
}

.card__btn-icono {
  width: 42px;
  height: 42px;
  border-radius: 50%;
  background-color: #f8f5f2;
  color: #471010;
  display: flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  transition: background-color 0.2s ease, transform 0.2s ease;
}

.card__btn-icono:hover {
  background-color: #ffffff;
  transform: scale(1.1);
}

/* Info */
.card__info {
  padding: 1.4rem 1.6rem 1.6rem;
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}

.card__nombre {
  font-family: 'Jost', sans-serif;
  font-size: 1.15rem;
  font-weight: 700;
  color: #471010;
}

.card__descripcion {
  font-size: 0.88rem;
  color: #6c533d;
  line-height: 1.65;
}

/* Tags */
.card__tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  list-style: none;
  padding: 0;
  margin-top: 0.4rem;
}

.card__tag {
  font-size: 0.78rem;
  color: #471010;
  border: 1px solid rgb(71 16 16 / 0.25);
  border-radius: 999px;
  padding: 0.2rem 0.7rem;
  transition: background-color 0.2s ease, border-color 0.2s ease;
}

.card:hover .card__tag {
  border-color: rgb(71 16 16 / 0.45);
}

/* Modo oscuro */
body.tema-oscuro .proyectos__titulo {
  color: #e8e0d8;
}

body.tema-oscuro .proyectos__linea {
  background-color: #496f49;
}

body.tema-oscuro .card {
  background-color: #2a2420;
  border-color: rgb(232 224 216 / 0.1);
}

body.tema-oscuro .card:hover {
  box-shadow: 0 16px 36px rgb(0 0 0 / 0.35);
}

body.tema-oscuro .card__imagen {
  filter: sepia(0.25) saturate(0.7) hue-rotate(330deg) brightness(0.75);
}

body.tema-oscuro .card__overlay {
  background-color: rgb(18 15 13 / 0.55);
}

body.tema-oscuro .card__btn-icono {
  background-color: #e8e0d8;
  color: #1a1612;
}

body.tema-oscuro .card__btn-icono:hover {
  background-color: #ffffff;
}

body.tema-oscuro .card__nombre {
  color: #e8e0d8;
}

body.tema-oscuro .card__descripcion {
  color: #c4a882;
}

body.tema-oscuro .card__tag {
  color: #e8e0d8;
  border-color: rgb(232 224 216 / 0.25);
}

body.tema-oscuro .card:hover .card__tag {
  border-color: rgb(232 224 216 / 0.45);
}

@media (width <= 600px) {
  .proyectos { padding: 4rem 1.5rem; }
  .card { width: 100%; max-width: 340px; }
}
</style>
