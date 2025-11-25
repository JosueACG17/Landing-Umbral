<template>
  <section id="app-movil" class="py-20 bg-black relative overflow-hidden">
    <!-- Efectos de fondo -->
    <div
      class="absolute inset-0 bg-[radial-gradient(circle_at_50%_50%,rgba(234,179,8,0.03),transparent_70%)]"
    ></div>
    <div
      class="absolute inset-0 pointer-events-none animate-pulse bg-gradient-to-tr from-yellow-700/10 via-transparent to-yellow-400/10"
    ></div>

    <!-- Contenido principal -->
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <!-- Encabezado con animación -->
      <div class="text-center mb-12 opacity-0 fade-in-up" ref="titleRef">
        <div class="flex items-center justify-center mb-4 space-x-4">
          <div
            class="h-[1px] w-20 bg-gradient-to-r from-transparent via-yellow-500 to-transparent"
          ></div>
          <h2
            class="text-4xl sm:text-5xl font-bold bg-gradient-to-r from-yellow-300 to-yellow-500 bg-clip-text text-transparent"
            style="font-family: 'Cinzel', serif"
          >
            NUESTRA APP
          </h2>
          <div
            class="h-[1px] w-20 bg-gradient-to-l from-transparent via-yellow-500 to-transparent"
          ></div>
        </div>
        <p class="text-xl text-yellow-200/90 mt-4" style="font-family: 'Montserrat', sans-serif">
          Experimenta la aventura en la palma de tu mano
        </p>
      </div>

      <!-- Grid con mockup de teléfono y features -->
      <div class="grid lg:grid-cols-2 gap-12 items-center">
        <!-- Mockup de teléfono 3D -->
        <div class="relative flex items-center justify-center perspective-1000">
          <!-- Efectos de fondo del teléfono -->
          <div
            class="absolute inset-0 bg-gradient-to-r from-yellow-500/20 via-yellow-400/10 to-yellow-500/20 blur-3xl animate-pulse"
          ></div>

          <!-- Círculos decorativos flotantes -->
          <div
            class="absolute top-1/4 -left-12 w-24 h-24 bg-yellow-500/10 rounded-full blur-2xl animate-float"
          ></div>
          <div
            class="absolute bottom-1/4 -right-12 w-32 h-32 bg-yellow-400/10 rounded-full blur-2xl animate-float-delayed"
          ></div>

          <!-- Contenedor del teléfono con transformación 3D -->
          <div class="relative phone-container opacity-0 fade-in" style="animation-delay: 0.3s">
            <!-- Marco del teléfono -->
            <div
              class="relative w-[300px] h-[600px] bg-black rounded-[50px] p-3 shadow-2xl transform-3d hover:rotate-y-5 transition-all duration-500"
            >
              <!-- Notch superior -->
              <div
                class="absolute top-0 left-1/2 -translate-x-1/2 w-1/2 h-7 bg-black rounded-b-3xl z-20"
              ></div>

              <!-- Brillo del marco -->
              <div
                class="absolute inset-0 rounded-[50px] border-2 border-yellow-500/30 shadow-[0_0_30px_rgba(234,179,8,0.3)]"
              ></div>
              <div class="absolute inset-[2px] rounded-[48px] border border-yellow-400/20"></div>

              <!-- Pantalla del teléfono -->
              <div class="relative w-full h-full bg-gray-900 rounded-[42px] overflow-hidden">
                <!-- Aquí va la imagen de tu app -->
                <img :src="appScreenshot" alt="App Screenshot" class="w-full h-full object-cover" />
              </div>
            </div>

            <!-- Sombra del teléfono -->
            <div
              class="absolute inset-0 top-8 bg-gradient-radial from-yellow-500/20 via-yellow-500/5 to-transparent blur-3xl -z-10"
            ></div>
          </div>
        </div>

        <!-- Features de la app -->
        <div class="space-y-8">
          <div
            v-for="(feature, index) in features"
            :key="index"
            class="flex gap-6 items-start opacity-0 fade-in-left group"
            :style="{ animationDelay: `${0.5 + index * 0.15}s` }"
          >
            <!-- Ícono -->
            <div class="relative flex-shrink-0">
              <div
                class="w-14 h-14 bg-gradient-to-br from-yellow-500/20 to-yellow-600/20 rounded-2xl flex items-center justify-center border border-yellow-500/30"
              >
                <div
                  class="absolute inset-0 bg-gradient-to-br from-yellow-400/0 to-yellow-500/20 rounded-2xl group-hover:from-yellow-400/20 transition-all duration-300"
                ></div>
                <component :is="feature.icon" class="relative z-10 h-8 w-8 animate-pulse" />
              </div>
              <!-- Glow effect -->
              <div
                class="absolute inset-0 bg-yellow-500/20 blur-xl rounded-full opacity-0 group-hover:opacity-100 transition-opacity duration-300"
              ></div>
            </div>

            <!-- Contenido -->
            <div class="flex-1">
              <h3
                class="text-xl font-bold bg-gradient-to-r from-yellow-300 to-yellow-500 bg-clip-text text-transparent mb-2 group-hover:from-yellow-400 group-hover:to-yellow-600 transition-all duration-300"
                style="font-family: 'Cinzel', serif"
              >
                {{ feature.title }}
              </h3>
              <p
                class="text-yellow-200/80 leading-relaxed group-hover:text-yellow-200 transition-colors duration-300"
                style="font-family: 'Montserrat', sans-serif"
              >
                {{ feature.description }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'

// IMPORTANDO HEROICONS VERDADEROS
import { SparklesIcon, ArrowPathIcon, BellAlertIcon, CloudIcon } from '@heroicons/vue/24/solid'

const titleRef = ref<HTMLElement | null>(null)

// Imagen temporal — cámbiala luego
const appScreenshot = ref('https://placehold.co/600x1200/1a1a1a/eab308?text=Tu+App+Aqui')

const features = [
  {
    title: 'Juega en Cualquier Lugar',
    description:
      'Lleva tu aventura contigo y juega donde quieras con controles optimizados para móvil.',
    icon: SparklesIcon,
  },
  {
    title: 'Sincronización en Tiempo Real',
    description: 'Tu progreso se sincroniza automáticamente entre todos tus dispositivos.',
    icon: ArrowPathIcon,
  },
  {
    title: 'Notificaciones Inteligentes',
    description:
      'Recibe alertas sobre eventos especiales, recompensas y actualizaciones importantes.',
    icon: BellAlertIcon,
  },
  {
    title: 'Modo Offline',
    description: 'Disfruta de ciertas características incluso sin conexión a internet.',
    icon: CloudIcon,
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
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes fadeInLeft {
  from {
    opacity: 0;
    transform: translateX(-30px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes shine {
  to {
    transform: translateX(100%);
  }
}

.animate-shine {
  animation: shine 3s infinite;
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-20px);
  }
}

@keyframes floatDelayed {
  0%,
  100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-15px);
  }
}

.animate-float {
  animation: float 6s ease-in-out infinite;
}

.animate-float-delayed {
  animation: floatDelayed 8s ease-in-out infinite;
  animation-delay: 1s;
}

.bg-gradient-radial {
  background: radial-gradient(circle, var(--tw-gradient-stops));
}
</style>
