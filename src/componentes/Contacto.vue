<script setup>
import { Mail, Phone, Github, Linkedin } from 'lucide-vue-next'

defineProps({
  contacto: Object,
})
</script>

<template>
  <section id="contacto" class="contacto">
    <h2 class="contacto__titulo">Contacto</h2>
    <div class="contacto__linea"></div>

    <p class="contacto__invitacion">¿Tienes algún proyecto en mente? ¡Hablemos!</p>

    <!-- Tarjetas -->
    <div class="contacto__tarjetas">
      <a :href="`mailto:${contacto.correo}`" class="tarjeta">
        <div class="tarjeta__icono">
          <Mail :size="24" color="#6c533d" />
        </div>
        <h3 class="tarjeta__titulo">Email</h3>
        <p class="tarjeta__dato">{{ contacto.correo }}</p>
      </a>

      <a :href="`tel:${contacto.telefono}`" class="tarjeta">
        <div class="tarjeta__icono">
          <Phone :size="24" color="#6c533d" />
        </div>
        <h3 class="tarjeta__titulo">Teléfono</h3>
        <p class="tarjeta__dato">{{ contacto.telefono }}</p>
      </a>
    </div>

    <!-- Redes sociales -->
    <p class="contacto__redes-titulo">Encuéntrame en redes sociales</p>

    <div class="contacto__redes">
      <a :href="contacto.github" target="_blank" rel="noopener noreferrer" class="red">
        <Github :size="22" color="#471010" />
      </a>
      <a :href="contacto.linkedin" target="_blank" rel="noopener noreferrer" class="red">
        <Linkedin :size="22" color="#471010" />
      </a>
    </div>
  </section>
</template>

<style scoped>
.contacto {
  background-color: #eae2da;
  padding: 5rem 4rem;
  text-align: center;
}

.contacto__titulo {
  font-size: 2.2rem;
  color: #471010;
  font-weight: 700;
  margin-bottom: 0.5rem;
}

.contacto__linea {
  width: 60px;
  height: 2px;
  background-color: #4d724d;
  margin: 0 auto 1.5rem;
}

.contacto__invitacion {
  color: #7d545a;
  font-size: 1rem;
  margin-bottom: 3rem;
}

/* Tarjetas */
.contacto__tarjetas {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1.5rem;
  margin-bottom: 3rem;
}

.tarjeta {
  text-decoration: none;
  background-color: #ffffff;
  border: 1px solid rgba(71, 16, 16, 0.1);
  border-radius: 16px;
  padding: 2rem 2.5rem;
  width: 220px;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.8rem;
}

.tarjeta:hover {
  transform: translateY(-6px);
  box-shadow: 0 12px 28px rgba(71, 16, 16, 0.1);
}

.tarjeta__icono {
  width: 56px;
  height: 56px;
  border-radius: 50%;
  background-color: rgba(161, 181, 161, 0.2);
  display: flex;
  align-items: center;
  justify-content: center;
}

.tarjeta__titulo {
  font-size: 1rem;
  font-weight: 700;
  color: #471010;
}

.tarjeta__dato {
  font-size: 0.85rem;
  color: #7d545a;
}

/* Redes */
.contacto__redes-titulo {
  color: #6c533d;
  font-size: 0.95rem;
  margin-bottom: 1.2rem;
}

.contacto__redes {
  display: flex;
  justify-content: center;
  gap: 1rem;
}

.red {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  border: 1px solid rgba(71, 16, 16, 0.15);
  display: flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  background-color: #ffffff;
  transition: transform 0.25s ease, box-shadow 0.25s ease, border-color 0.25s ease;
}

.red:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 20px rgba(71, 16, 16, 0.1);
  border-color: #6c533d;
}

@media (max-width: 480px) {
  .contacto { padding: 4rem 1.5rem; }
  .contacto__tarjetas { flex-direction: column; align-items: center; }
  .tarjeta { width: 100%; max-width: 300px; }
}
</style>