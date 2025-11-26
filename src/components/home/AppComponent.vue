<template>
  <section id="app-movil" class="py-20 bg-black relative overflow-hidden">

    <!-- FONDO -->
    <div class="absolute inset-0 bg-[radial-gradient(circle_at_50%_50%,rgba(234,179,8,0.03),transparent_70%)]"></div>
    <div class="absolute inset-0 pointer-events-none animate-pulse bg-gradient-to-tr from-yellow-700/10 via-transparent to-yellow-400/10"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">

      <!-- ENCABEZADO -->
      <div class="text-center mb-12 opacity-0 fade-in-up" ref="titleRef">
        <div class="flex items-center justify-center mb-4 space-x-4">
          <div class="h-[1px] w-20 bg-gradient-to-r from-transparent via-yellow-500 to-transparent"></div>
          <h2
            class="text-4xl sm:text-5xl font-bold bg-gradient-to-r from-yellow-300 to-yellow-500 bg-clip-text text-transparent"
            style="font-family: 'Cinzel', serif"
          >
            NUESTRA APP
          </h2>
          <div class="h-[1px] w-20 bg-gradient-to-l from-transparent via-yellow-500 to-transparent"></div>
        </div>
        <p class="text-xl text-yellow-200/90 mt-4" style="font-family: 'Montserrat', sans-serif">
          Experimenta la aventura en la palma de tu mano
        </p>
      </div>

      <!-- GRID PRINCIPAL -->
      <div class="grid lg:grid-cols-2 gap-12 items-center">

        <!-- COLUMNA IZQUIERDA -->
        <div class="relative flex items-center justify-center perspective-1000">

          <!-- MANO (solo desktop) -->
          <div
            class="hidden lg:block absolute bottom-0 left-1/2 -translate-x-[50%] translate-y-[50%] w-[527px] pointer-events-none z-10 hand-hold"
          >
            <img :src="handHoldImage" alt="Hand" class="w-full opacity-100" />
          </div>

          <!-- TELÉFONO (desktop: flotando; móvil: centrado arriba de features) -->
          <div
            class="phone-container opacity-100"
            :class="{
              'absolute left-1/2 top-[28%] -translate-x-1/2 -translate-y-1/2 z-30': isDesktop,
              'mx-auto mb-10': !isDesktop
            }"
          >
            <div
              class="relative w-[220px] h-[450px] bg-black rounded-[45px] p-3 shadow-2xl transform-3d hover:rotate-y-5 transition-all duration-500"
            >

              <div class="absolute inset-0 rounded-[45px] border-2 border-yellow-500/30 shadow-[0_0_30px_rgba(234,179,8,0.3)]"></div>
              <div class="absolute inset-[2px] rounded-[43px] border border-yellow-400/20"></div>

              <div class="relative w-full h-full bg-gray-900 rounded-[40px] overflow-hidden">
                <img :src="appScreenshot" alt="App Screenshot" class="w-full h-full object-cover" />
              </div>
            </div>
          </div>

        </div>

        <!-- FEATURES -->
        <div class="space-y-8">
          <div
            v-for="(feature, index) in features"
            :key="index"
            class="flex gap-6 items-start opacity-0 fade-in-left group"
            :style="{ animationDelay: `${0.5 + index * 0.15}s` }"
          >
            <div class="relative flex-shrink-0">
              <div class="w-14 h-14 bg-gradient-to-br from-yellow-500/20 to-yellow-600/20 rounded-2xl flex items-center justify-center border border-yellow-500/30">
                <div class="absolute inset-0 bg-gradient-to-br from-yellow-400/0 to-yellow-500/20 rounded-2xl group-hover:from-yellow-400/20 transition-all duration-300"></div>
                <component :is="feature.icon" class="relative z-10 h-8 w-8 animate-pulse" />
              </div>
            </div>

            <div class="flex-1">
              <h3
                class="text-xl font-bold bg-gradient-to-r from-yellow-300 to-yellow-500 bg-clip-text text-transparent mb-2"
                style="font-family: 'Cinzel', serif"
              >
                {{ feature.title }}
              </h3>
              <p
                class="text-yellow-200/80 leading-relaxed group-hover:text-yellow-200 transition-colors duration-300 text-sm lg:text-base"
                style="font-family: 'Montserrat', sans-serif"
              >
                {{ feature.description }}
              </p>
            </div>
          </div>

          <!-- Botón -->
          <div class="mt-10 flex justify-center lg:justify-start">
            <a
              href="https://github.com/eduardo87DR/Umbral-App/releases/download/v1.0.0/app-release.apk"
              target="_blank"
              class="group relative px-10 py-4 rounded-2xl font-bold text-lg text-black bg-yellow-400 shadow-[0_0_25px_rgba(234,179,8,0.5)] hover:shadow-[0_0_45px_rgba(234,179,8,0.8)] transition-all duration-300 overflow-hidden"
              style="font-family: 'Cinzel', serif"
            >
              <span class="relative z-10" style="font-family: 'Montserrat', sans-serif">Descargar App</span>
              <div class="absolute inset-0 bg-gradient-to-r from-yellow-300 via-yellow-500 to-yellow-300 opacity-0 group-hover:opacity-20 transition-opacity duration-300"></div>
              <div class="absolute top-0 left-0 w-1/3 h-full bg-white/40 blur-xl translate-x-[-150%] group-hover:translate-x-[250%] transition-transform duration-700"></div>
            </a>
          </div>

        </div>
      </div>
    </div>
  </section>
</template>
<script setup lang="ts">
import { ref, onMounted } from 'vue'
import {
  CalendarDaysIcon,
  BookOpenIcon,
  BellAlertIcon,
  ChartBarIcon,
} from '@heroicons/vue/24/solid'

import AppUmbral from '../../../public/Umbral2.jpg'
import HandHold from '@/assets/Mano.png'

const titleRef = ref<HTMLElement | null>(null)
const appScreenshot = ref(AppUmbral)
const handHoldImage = ref(HandHold)

const isDesktop = ref(false)

onMounted(() => {
  const update = () => {
    isDesktop.value = window.innerWidth >= 1024
  }
  update()
  window.addEventListener('resize', update)
})

const features = [
  {
    title: 'Eventos del Juego',
    description:
      'Consulta los eventos activos, revisa sus detalles y mantente actualizado con todo lo que sucede en el mundo del Umbral.',
    icon: CalendarDaysIcon,
  },
  {
    title: 'Guías Oficiales',
    description:
      'Explora guías oficiales y comparte tu experiencia comentando. Aprende, mejora y participa junto con la comunidad.',
    icon: BookOpenIcon,
  },
  {
    title: 'Notificaciones Relevantes',
    description: 'Recibe alertas sobre avisos importantes del juego.',
    icon: BellAlertIcon,
  },
  {
    title: 'Estadísticas y Rankings',
    description:
      'Consulta rankings, tus avances y perfil clave que reflejan tu progreso dentro del juego.',
    icon: ChartBarIcon,
  },
]
</script>
<style scoped>
.bg-clip-text {
  -webkit-background-clip: text;
  background-clip: text;
}

.perspective-1000 {
  perspective: 1000px;
}
.transform-3d {
  transform-style: preserve-3d;
  transition: transform 0.6s ease;
}
.rotate-y-5 {
  transform: rotateY(5deg) rotateX(-2deg);
}

.phone-container:hover .transform-3d {
  transform: rotateY(5deg) rotateX(-2deg) translateY(-8px);
}

.hand-hold {
  transform-origin: bottom center;
  transition: transform 0.4s ease;
}

@media (min-width: 1024px) {
  .phone-container:hover ~ .hand-hold {
    transform: translateY(-6px) rotate(-2deg) scale(1.02);
  }
}

/* Animaciones */
.fade-in-up {
  animation: fadeInUp 1s ease-out forwards;
}
.fade-in {
  animation: fadeIn 1s ease-out forwards;
}
.fade-in-left {
  animation: fadeInLeft 0.8s ease-out forwards;
}

@keyframes fadeInUp {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}
@keyframes fadeInLeft {
  from { opacity: 0; transform: translateX(-30px); }
  to { opacity: 1; transform: translateX(0); }
}

</style>
