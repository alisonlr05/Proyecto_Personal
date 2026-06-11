<script setup>
import { Mail, Phone, Github, Linkedin, Cpu } from 'lucide-vue-next'

defineProps({
  contacto: Object,
})
</script>

<template>
  <section id="contacto" class="contacto">

    <div class="contacto__deco">
  <!-- HTML5 -->
  <div class="deco-bg deco-bg--1">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
      <path d="M4 3l1.5 17L12 22l6.5-2L20 3H4z"/>
      <path d="M16 8H8l.5 4.5h7l-.5 5-3 1-3-1-.2-2.5"/>
    </svg>
  </div>

  <!-- CSS3 -->
  <div class="deco-bg deco-bg--2">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
      <path d="M4 3l1.5 17L12 22l6.5-2L20 3H4z"/>
      <path d="M16.5 8h-9l.4 4h8.2l-.6 5.5-3.5 1-3.5-1-.2-2.5"/>
    </svg>
  </div>

  <!-- JavaScript -->
  <div class="deco-bg deco-bg--3">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
      <rect x="3" y="3" width="18" height="18" rx="2"/>
      <path d="M8 17c0 1.5 2.5 2 3 0V12"/>
      <path d="M13 12h4M15 12v5"/>
    </svg>
  </div>

  <!-- Vue -->
  <div class="deco-bg deco-bg--4">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
      <path d="M2 4l10 16L22 4h-4l-6 10L8 4H2z"/>
      <path d="M6 4l6 10 6-10h-3l-3 5-3-5H6z"/>
    </svg>
  </div>

  <!-- GitHub -->
  <div class="deco-bg deco-bg--5">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
      <path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"/>
    </svg>
  </div>

  <!-- Base de datos -->
  <div class="deco-bg deco-bg--6">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
      <ellipse cx="12" cy="5" rx="9" ry="3"/>
      <path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"/>
      <path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"/>
    </svg>
  </div>

  <!-- Nube -->
  <div class="deco-bg deco-bg--7">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
      <path d="M18 10h-1.26A8 8 0 1 0 9 20h9a5 5 0 0 0 0-10z"/>
    </svg>
  </div>
</div>

<!-- Cpu -->
    <div class="deco-bg deco-bg--cpu">
      <Cpu :size="36" />
    </div>


    <h2 class="contacto__titulo">Contacto</h2>
    <div class="contacto__linea"></div>

    <p class="contacto__invitacion">¿Tienes algún proyecto en mente? ¡Hablemos!</p>

    <!-- Tarjetas -->
    <div class="contacto__tarjetas">
      <a :href="`mailto:${contacto.correo}`" class="tarjeta">
        <div class="tarjeta__icono">
          <Mail :size="24" class="tarjeta__svg" />
        </div>
        <h3 class="tarjeta__titulo">Email</h3>
        <p class="tarjeta__dato">{{ contacto.correo }}</p>
      </a>

      <a :href="`tel:${contacto.telefono}`" class="tarjeta">
        <div class="tarjeta__icono">
          <Phone :size="24" class="tarjeta__svg" />
        </div>
        <h3 class="tarjeta__titulo">Teléfono</h3>
        <p class="tarjeta__dato">{{ contacto.telefono }}</p>
      </a>
    </div>

    <!-- Redes sociales -->
    <p class="contacto__redes-titulo">Encuéntrame en otras redes</p>
    <div class="contacto__redes">
      <a :href="contacto.github" target="_blank" rel="noopener noreferrer" class="red">
        <Github :size="22" class="red__icono" />
      </a>
      <a :href="contacto.linkedin" target="_blank" rel="noopener noreferrer" class="red">
        <Linkedin :size="22" class="red__icono" />
      </a>
    </div>
  </section>
</template>

<style scoped>
.contacto {
  background-color: #e0dcd8;
  padding: 5rem 4rem;
  text-align: center;
  position: relative;
  overflow: hidden;
}

.contacto__titulo {
  font-family: 'Playfair Display', serif;
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
  color: #64383d;
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
  font-family: 'Jost', sans-serif;
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

.tarjeta__svg {
  color: #6c533d;
  transition: color 0.3s ease;
}

.red__icono {
  color: #6e3636;
  transition: color 0.3s ease;
}

/* Modo oscuro */
body.tema-oscuro .contacto {
  background-color: #120f0d;
}

body.tema-oscuro .contacto__titulo {
  color: #e8e0d8;
}

body.tema-oscuro .contacto__linea {
  background-color: #496f49;
}

body.tema-oscuro .contacto__invitacion {
  color: #c49aa0;
}

body.tema-oscuro .tarjeta {
  background-color: #2a2420;
  border-color: rgba(232, 224, 216, 0.1);
}

body.tema-oscuro .tarjeta:hover {
  box-shadow: 0 12px 28px rgba(0, 0, 0, 0.3);
}

body.tema-oscuro .tarjeta__icono {
  background-color: rgba(161, 133, 106, 0.2);
}

body.tema-oscuro .tarjeta__svg {
  color: #a1856a;
}

body.tema-oscuro .tarjeta__titulo {
  color: #e8e0d8;
}

body.tema-oscuro .tarjeta__dato {
  color: #c49aa0;
}

body.tema-oscuro .contacto__redes-titulo {
  color: #a1856a;
}

body.tema-oscuro .red {
  background-color: #2a2420;
  border-color: rgba(232, 224, 216, 0.15);
}

body.tema-oscuro .red:hover {
  border-color: #a1856a;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
}

body.tema-oscuro .red__icono {
  color: #e8e0d8;
}

.contacto__deco {
  position: absolute;
  inset: 0;
  pointer-events: none;
}

.deco-bg--cpu {
  position: absolute;
  left: 15%;
  top: 45%;
  opacity: 0.15;
  color: #331010;
  animation: flotar2 7s ease-in-out infinite;
  transition: color 0.3s ease, opacity 0.3s ease;
}

body.tema-oscuro .deco-bg--cpu {
  color: #a1b5a1;
  opacity: 0.25;
}

.deco-bg {
  position: absolute;
  opacity: 0.12;
  color: #331010;
  transition: color 0.3s ease, opacity 0.3s ease;
}

body.tema-oscuro .deco-bg {
  color: #a1b5a1;
  opacity: 0.2;
}

.deco-bg svg { width: 100%; height: 100%; }

.deco-bg--1 { width: 48px; height: 48px; top: 10%;  left: 5%;   animation: flotar1 6s ease-in-out infinite; }
.deco-bg--2 { width: 38px; height: 38px; top: 75%;  left: 8%;   animation: flotar2 7s ease-in-out infinite; }
.deco-bg--3 { width: 44px; height: 44px; top: 15%;  right: 6%;  animation: flotar3 5s ease-in-out infinite; }
.deco-bg--4 { width: 52px; height: 52px; top: 60%;  right: 5%;  animation: flotar1 8s ease-in-out infinite; }
.deco-bg--5 { width: 40px; height: 40px; top: 85%;  left: 25%;  animation: flotar2 6s ease-in-out infinite; }
.deco-bg--6 { width: 36px; height: 36px; top: 20%;  right: 20%; animation: flotar3 7s ease-in-out infinite; }
.deco-bg--7 { width: 56px; height: 56px; top: 70%;  right: 15%; animation: flotar1 9s ease-in-out infinite; }

@keyframes flotar1 {
  0%, 100% { transform: translateY(0px);   }
  50%       { transform: translateY(-12px); }
}
@keyframes flotar2 {
  0%, 100% { transform: translateY(0px)  rotate(0deg);  }
  50%       { transform: translateY(-8px) rotate(5deg);  }
}
@keyframes flotar3 {
  0%, 100% { transform: translateY(0px)   rotate(0deg);  }
  50%       { transform: translateY(-10px) rotate(-5deg); }
}
</style>