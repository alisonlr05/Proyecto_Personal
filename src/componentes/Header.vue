<script setup>
import { ref, onMounted, nextTick } from 'vue'
import { Sun, Moon, Cpu } from 'lucide-vue-next'

const props = defineProps({
  nombre:     String,
  temaOscuro: Boolean,
})

defineEmits(['toggleTema'])

const activo    = ref('inicio')
const burbujaEl = ref(null)
const itemsEl   = ref([])
let   lastRect  = null

const secciones = [
  { label: 'Inicio',    id: 'inicio'    },
  { label: 'Sobre Mí', id: 'sobre-mi'  },
  { label: 'Skills',   id: 'skills'    },
  { label: 'Proyectos',id: 'proyectos' },
  { label: 'Contacto', id: 'contacto'  },
]

function navegar(id, index) {
  const anteriorRect = lastRect
  activo.value = id
  const el = document.getElementById(id)
  if (el) el.scrollIntoView({ behavior: 'smooth' })

  nextTick(() => {
    const itemActivo = itemsEl.value[index]
    if (!itemActivo || !burbujaEl.value) return

    const nuevoRect = itemActivo.getBoundingClientRect()
    const navRect   = itemActivo.parentElement.getBoundingClientRect()
    const x = nuevoRect.left - navRect.left
    const w = nuevoRect.width

    if (anteriorRect) {
      const dx = anteriorRect.x - x
      burbujaEl.value.animate(
        [
          { transform: `translateX(${dx}px) scaleX(${anteriorRect.w / w})`, opacity: 1 },
          { transform: 'translateX(0px) scaleX(1)', opacity: 1 },
        ],
        { duration: 300, easing: 'cubic-bezier(0.5, 0, 0.5, 1)', fill: 'forwards' }
      )
    }

    lastRect = { x, w }
    burbujaEl.value.style.left  = x + 'px'
    burbujaEl.value.style.width = w + 'px'
  })
}

onMounted(() => {
  nextTick(() => {
    const primerItem = itemsEl.value[0]
    if (!primerItem || !burbujaEl.value) return
    const rect    = primerItem.getBoundingClientRect()
    const navRect = primerItem.parentElement.getBoundingClientRect()
    const x = rect.left - navRect.left
    burbujaEl.value.style.left  = x + 'px'
    burbujaEl.value.style.width = rect.width + 'px'
    lastRect = { x, w: rect.width }
  })
})
</script>

<template>
  <header class="header">
    <div class="header__logo">
  <Cpu :size="18" color="#6c533d" />
  <span>Portfolio Personal</span>
</div>

    <nav class="header__nav">
      <span class="nav__burbuja" ref="burbujaEl"></span>

      <a
        v-for="(s, i) in secciones"
        :key="s.id"
        :href="`#${s.id}`"
        :ref="el => itemsEl[i] = el"
        class="nav__item"
        :class="{ 'nav__item--activo': activo === s.id }"
        @click.prevent="navegar(s.id, i)"
      >
        <span class="nav__label">{{ s.label }}</span>
      </a>
    </nav>

    <!-- Toggle tema -->
    <button class="toggle__tema" @click="$emit('toggleTema')">
      <span class="toggle__pista" :class="{ 'toggle__pista--oscuro': temaOscuro }">
        <span class="toggle__circulo" :class="{ 'toggle__circulo--oscuro': temaOscuro }">
          <Sun v-if="!temaOscuro" :size="14" color="#6c533d" />
          <Moon v-else            :size="14" color="#f8f5f2" />
        </span>
      </span>
    </button>
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
  padding: 1rem 4rem;
  background-color: #e0dcd8;
  border-bottom: 1px solid rgba(71, 16, 16, 0.08);
  transition: background-color 0.3s ease;
}

.header__logo {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-weight: 600;
  color: #471010;
  font-size: 1rem;
  letter-spacing: 0.02em;
  flex-shrink: 0;
  transition: color 0.3s ease;
}

.header__icono {
  color: #6c533d;
  font-size: 1rem;
}

.header__nav {
  position: relative;
  display: flex;
  align-items: center;
  gap: 0.1rem;
}

.nav__burbuja {
  position: absolute;
  top: 0;
  height: 100%;
  border-radius: 999px;
  background-color: #6c533d;
  z-index: 0;
  pointer-events: none;
  will-change: transform, width;
}

.nav__item {
  position: relative;
  display: flex;
  align-items: center;
  background: none;
  border: none;
  cursor: pointer;
  text-decoration: none;
  padding: 0.4rem 0.8rem;
  border-radius: 999px;
  font-family: inherit;
  font-size: 0.85rem;
  font-weight: 400;
  color: #471010;
  letter-spacing: 0.01em;
  z-index: 1;
  transition: color 0.25s ease;
  white-space: nowrap;
}

.nav__item--activo .nav__label {
  color: #f8f5f2;
  font-weight: 500;
}

.nav__item:not(.nav__item--activo):hover .nav__label {
  color: #6c533d;
}

/* Toggle */
.toggle__tema {
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
  flex-shrink: 0;
}

.toggle__pista {
  display: flex;
  align-items: center;
  width: 52px;
  height: 28px;
  border-radius: 999px;
  border: 2px solid rgba(71, 16, 16, 0.2);
  background-color: #f8f5f2;
  padding: 3px;
  transition: background-color 0.3s ease, border-color 0.3s ease;
}

.toggle__pista--oscuro {
  background-color: #2a2420;
  border-color: rgba(232, 224, 216, 0.2);
}

.toggle__circulo {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color: #e0dcd8;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.3s cubic-bezier(0.5, 0, 0.5, 1), background-color 0.3s ease;
}

.toggle__circulo--oscuro {
  transform: translateX(24px);
  background-color: #6c533d;
}

/* Tablet */
@media (max-width: 768px) {
  .header {
    padding: 0.8rem 1.5rem;
    flex-direction: column;
    gap: 0.5rem;
  }
}

/* Móvil pequeño */
@media (max-width: 480px) {
  .header {
    padding: 0.6rem 0.5rem;
  }

  .nav__item {
    padding: 0.35rem 0.5rem;
    font-size: 0.75rem;
  }
}

/* Modo oscuro */
body.tema-oscuro .header {
  background-color: #120f0d;
  border-bottom-color: rgba(232, 224, 216, 0.08);
}

body.tema-oscuro .header__logo {
  color: #e8e0d8;
}

body.tema-oscuro .header__icono {
  color: #a1856a;
}

body.tema-oscuro .nav__item {
  color: #e8e0d8;
}

body.tema-oscuro .nav__item:not(.nav__item--activo):hover .nav__label {
  color: #a1856a;
}

body.tema-oscuro .nav__burbuja {
  background-color: #a1856a;
}

body.tema-oscuro .toggle__pista {
  background-color: #2a2420;
  border-color: rgba(232, 224, 216, 0.2);
}
</style>