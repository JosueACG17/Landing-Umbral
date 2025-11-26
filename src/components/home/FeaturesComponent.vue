<template>
  <section id="caracteristicas" class="py-32 bg-black relative overflow-hidden" ref="sectionRef">
    <!-- Background effects -->
    <div
      class="absolute inset-0 bg-[radial-gradient(circle_at_30%_20%,rgba(234,179,8,0.08),transparent_50%)]"
    ></div>
    <div
      class="absolute inset-0 bg-[radial-gradient(circle_at_70%_80%,rgba(234,179,8,0.08),transparent_50%)]"
    ></div>
    <div
      class="absolute inset-0 opacity-20"
      style="
        background-image: radial-gradient(rgba(234, 179, 8, 0.1) 1px, transparent 1px);
        background-size: 50px 50px;
      "
    ></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <!-- Header -->
      <div class="text-center mb-20 opacity-0" :class="{ 'fade-in-up': isIntersecting }">
        <p class="text-yellow-400 text-base tracking-[0.3em] uppercase mb-4 font-light">
          CARACTERÍSTICAS DEL JUEGO
        </p>

        <h2
          class="text-5xl sm:text-6xl md:text-7xl lg:text-8xl font-black text-transparent bg-clip-text bg-gradient-to-b from-yellow-300 via-yellow-400 to-yellow-600 mb-4 tracking-tight leading-none"
          style="text-shadow: 0 0 40px rgba(234, 179, 8, 0.3); font-family: 'Cinzel', serif"
        >
          MECÁNICAS
        </h2>

        <p class="text-gray-400 text-lg max-w-2xl mx-auto font-light leading-relaxed">
          Mecánicas esenciales que definen la experiencia en UMBRAL
        </p>
      </div>

      <!-- Cards -->
      <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
        <div
          v-for="(feature, index) in features"
          :key="index"
          class="group relative overflow-hidden rounded-2xl backdrop-blur-sm bg-gradient-to-br from-zinc-900/60 to-black/50 border border-yellow-900/60 hover:border-yellow-500/50 transition-all duration-700 opacity-0 hover:scale-[1.02] hover:shadow-2xl hover:shadow-yellow-500/10"
          :class="{ 'slide-in-up': isIntersecting }"
          :style="{ 'animation-delay': `${0.15 * (index + 1)}s` }"
        >
          <div
            class="absolute inset-0 bg-gradient-to-br from-yellow-500/0 via-yellow-500/0 to-yellow-500/0 group-hover:from-yellow-500/5 group-hover:via-transparent group-hover:to-yellow-600/5 transition-all duration-700"
          ></div>
          <div
            class="absolute -inset-0.5 bg-gradient-to-r from-yellow-500 to-yellow-600 rounded-2xl opacity-0 group-hover:opacity-20 blur-xl transition-opacity duration-700"
          ></div>

          <div class="relative p-16">
            <!-- Icon -->
            <div class="mb-6 relative">
              <div
                class="absolute inset-0 bg-yellow-500/20 blur-3xl opacity-0 group-hover:opacity-100 transition-opacity duration-700"
              ></div>

              <div
                class="relative w-20 h-20 mx-auto rounded-2xl bg-gradient-to-br from-yellow-500/10 to-yellow-600/10 border border-yellow-500/20 flex items-center justify-center backdrop-blur-sm group-hover:scale-110 group-hover:bg-gradient-to-br group-hover:from-yellow-500/20 group-hover:to-yellow-600/20 transition-all duration-700"
              >
                <component
                  :is="feature.icon"
                  class="w-12 h-12 text-yellow-400 transition-all duration-700 group-hover:scale-110"
                />
              </div>
            </div>

            <!-- Title -->
            <h3
              class="text-2xl font-bold text-white mb-4 text-center group-hover:text-yellow-400 transition-colors duration-500 tracking-tight"
              style="font-family: 'Cinzel', serif"
            >
              {{ feature.title }}
            </h3>

            <!-- Description -->
            <p
              class="text-gray-400 text-center leading-relaxed font-light text-sm group-hover:text-gray-300 transition-colors duration-500"
            >
              {{ feature.description }}
            </p>
          <!-- Decorative corner accents -->
            <div class="absolute top-4 left-4 w-8 h-8 border-t-2 border-l-2 border-yellow-500/0 group-hover:border-yellow-500/50 rounded-tl-lg transition-all duration-700"></div>
            <div class="absolute bottom-4 right-4 w-8 h-8 border-b-2 border-r-2 border-yellow-500/0 group-hover:border-yellow-500/50 rounded-br-lg transition-all duration-700"></div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { UserGroupIcon, MapIcon, BoltIcon } from '@heroicons/vue/24/solid'
import { useIntersectionObserver } from '@/composables/useIntersectionObserver'

const features = [
  {
    title: 'Selección de Personaje',
    description:
      'El jugador elige uno de los Cuatro Caballeros de Umbral, cada uno con un estilo de combate único.',
    icon: UserGroupIcon,
  },
  {
    title: 'Exploración y Combate',
    description:
      'Avanza por la mazmorra enfrentando oleadas de enemigos mientras te posicionas estratégicamente.',
    icon: MapIcon,
  },
  {
    title: 'Acciones del Jugador',
    description:
      'Muévete libremente (WASD) y ejecuta ataques principales según tu clase: espada, flecha, hacha o magia.',
    icon: BoltIcon,
  },
]

const { isIntersecting, target: sectionRef } = useIntersectionObserver()
</script>

<style scoped>
.fade-in-up {
  animation: fadeInUp 1s ease-out forwards;
}
.slide-in-up {
  animation: slideInUp 0.8s ease-out forwards;
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
@keyframes slideInUp {
  from {
    opacity: 0;
    transform: translateY(40px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
@keyframes shimmer {
  0% {
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(300%);
  }
}
.animate-shimmer {
  animation: shimmer 2s infinite;
}
</style>
