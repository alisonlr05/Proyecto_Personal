<script setup>
defineProps({
  habilidades: Array,
})
</script>

<template>
  <section id="skills" class="skills">
    <h2 class="skills__titulo">Skills</h2>
    <div class="skills__linea"></div>

    <div class="skills__grid">
      <div
        v-for="skill in habilidades"
        :key="skill.nombre"
        class="skill-card"
      >
        <!-- Marco SVG animado -->
        <svg class="skill-card__frame" viewBox="0 0 180 120" preserveAspectRatio="none">
          <path class="frame-path" d="M 10,10 H 170 V 110 H 10 Z" />
        </svg>

        <p class="skill-card__categoria">{{ skill.categoria }}</p>
        <h3 class="skill-card__nombre">{{ skill.nombre }}</h3>
      </div>
    </div>
  </section>
</template>

<style scoped>
.skills {
  background-color: #f8f5f2;
  padding: 5rem 4rem;
  text-align: center;
}

.skills__titulo {
  font-size: 2.2rem;
  color: #471010;
  font-weight: 700;
  margin-bottom: 0.5rem;
}

.skills__linea {
  width: 60px;
  height: 2px;
  background-color: #6c533d;
  margin: 0 auto 3rem;
}

.skills__grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1.5rem;
  max-width: 900px;
  margin: 0 auto;
}

.skill-card {
  position: relative;
  background-color: #ffffff;
  border: 1px solid rgba(71, 16, 16, 0.1);
  border-radius: 12px;
  padding: 1.8rem 2rem;
  width: 180px;
  text-align: center;
  cursor: default;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
}

.skill-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 28px rgba(71, 16, 16, 0.12);
}

/* Marco SVG */
.skill-card__frame {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  border-radius: 12px;
}

.frame-path {
  fill: none;
  stroke: #6c533d;
  stroke-width: 1.5;
  stroke-dasharray: 520;
  stroke-dashoffset: 520;
  transition: stroke-dashoffset 0.8s cubic-bezier(0.16, 1, 0.3, 1);
}

.skill-card:hover .frame-path {
  stroke-dashoffset: 0;
}

.skill-card__categoria {
  font-size: 0.72rem;
  color: #a1b5a1;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  margin-bottom: 0.8rem;
}

.skill-card__nombre {
  font-size: 1.1rem;
  color: #471010;
  font-weight: 600;
}
</style>