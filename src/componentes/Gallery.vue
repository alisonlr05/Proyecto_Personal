<script setup>
defineProps({
  proyectos: Array,
})
</script>

<template>
  <section id="proyectos" class="proyectos">
    <h2 class="proyectos__titulo">Proyectos</h2>
    <div class="proyectos__linea"></div>

    <div class="proyectos__grid">
      <div
        v-for="proyecto in proyectos"
        :key="proyecto.nombre"
        class="card"
      >
        <!-- Frente -->
        <div class="card__lado card__lado--frente">
          <div class="card__contenido">
            <h3 class="card__nombre">{{ proyecto.nombre }}</h3>
            <p class="card__descripcion">{{ proyecto.descripcion }}</p>
          </div>
        </div>

        <!-- Reverso -->
        <div class="card__lado card__lado--reverso">
          <div class="card__cta">
            <a :href="proyecto.link" target="_blank" rel="noopener noreferrer" class="card__btn">
              Ver proyecto
            </a>
          </div>
        </div>
      </div>
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
  gap: 2.5rem;
  max-width: 1000px;
  margin: 0 auto;
}

/* Tarjeta */
.card {
  perspective: 150rem;
  position: relative;
  width: 300px;
  height: 380px;
}

.card__lado {
  position: absolute;
  top: 0; left: 0;
  width: 100%;
  height: 100%;
  border-radius: 12px;
  overflow: hidden;
  backface-visibility: hidden;
  transition: transform 0.8s ease;
  box-shadow: 0 1.5rem 4rem rgba(71, 16, 16, 0.15);
}

/* Frente */
.card__lado--frente {
  background: linear-gradient(-45deg, #6c533d, #a1b5a1);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2.5rem;
}

.card__contenido {
  text-align: center;
}

.card__nombre {
  font-family: 'Jost', sans-serif;
  font-size: 1.8rem;
  font-weight: 700;
  color: #f8f5f2;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 1.2rem;
}

.card__descripcion {
  font-size: 0.9rem;
  color: rgba(248, 245, 242, 0.85);
  line-height: 1.7;
}

/* Reverso */
.card__lado--reverso {
  background: linear-gradient(-45deg, #7d545a, #6c533d);
  transform: rotateY(180deg);
  display: flex;
  align-items: center;
  justify-content: center;
}

.card__cta {
  text-align: center;
}

.card__btn {
  display: inline-block;
  padding: 0.9rem 2.5rem;
  background-color: #f8f5f2;
  color: #471010;
  text-decoration: none;
  border-radius: 999px;
  font-size: 0.95rem;
  font-weight: 600;
  letter-spacing: 0.05em;
  transition: all 0.25s ease;
}

.card__btn:hover {
  background-color: #471010;
  color: #f8f5f2;
  transform: translateY(-3px);
  box-shadow: 0 1rem 2rem rgba(0, 0, 0, 0.2);
}

/* Animación de volteo */
.card:hover .card__lado--frente {
  transform: rotateY(-180deg);
}

.card:hover .card__lado--reverso {
  transform: rotateY(0);
}

/* Modo oscuro */
body.tema-oscuro .proyectos__titulo {
  color: #e8e0d8;
}

body.tema-oscuro .proyectos__linea {
  background-color: #496f49;
}
</style>