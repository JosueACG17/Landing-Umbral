<template>
  <section
    id="informacion"
    class="py-20 bg-gradient-to-b from-black via-gray-950 to-black relative overflow-hidden"
    ref="sectionRef"
  >
    <!-- Efectos de fondo -->
    <div
      class="absolute inset-0 bg-[radial-gradient(circle_at_50%_50%,rgba(234,179,8,0.03),transparent_70%)]"
    ></div>
    <div
      class="absolute inset-0 pointer-events-none animate-pulse bg-gradient-to-tr from-yellow-700/10 via-transparent to-yellow-400/10"
    ></div>

    <!-- Partículas de fondo -->
    <div class="absolute inset-0 opacity-30">
      <div
        v-for="n in 20"
        :key="n"
        class="particle-star"
        :style="{
          left: `${Math.random() * 100}%`,
          top: `${Math.random() * 100}%`,
          animationDelay: `${Math.random() * 5}s`,
        }"
      ></div>
    </div>

    <!-- Contenido principal -->
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <!-- Encabezado de la sección -->
      <div class="text-center mb-16 opacity-0" :class="{ 'fade-in-up': isIntersecting }">
        <div class="flex items-center justify-center mb-4 space-x-4">
          <div
            class="h-[1px] w-20 bg-gradient-to-r from-transparent via-yellow-500 to-transparent"
          ></div>
          <h2
            class="text-4xl sm:text-5xl font-bold bg-gradient-to-r from-yellow-300 to-yellow-500 bg-clip-text text-transparent"
            style="font-family: 'Cinzel', serif"
          >
            CARACTERÍSTICAS
          </h2>
          <div
            class="h-[1px] w-20 bg-gradient-to-l from-transparent via-yellow-500 to-transparent"
          ></div>
        </div>
        <p class="text-xl text-yellow-200/90 mt-4" style="font-family: 'Montserrat', sans-serif">
          Sumérgete en un mundo de fantasía oscura
        </p>
      </div>

      <!-- Grid de características -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
        <!-- Columna de tarjetas de características -->
        <div class="space-y-8">
          <div
            v-for="(feature, index) in features"
            :key="index"
            class="group relative overflow-hidden rounded-xl p-6 opacity-0"
            :class="{ 'slide-in-left': isIntersecting }"
            :style="{ 'animation-delay': `${0.2 * (index + 1)}s` }"
          >
            <!-- Fondo con efecto de brillo -->
            <div
              class="absolute inset-0 bg-gradient-to-br from-black/90 via-black/70 to-yellow-900/30 transition-all duration-500 group-hover:from-black/80 group-hover:to-yellow-900/40"
            ></div>
            <div
              class="absolute inset-0 opacity-0 group-hover:opacity-100 transition-opacity duration-500 bg-[radial-gradient(circle_at_50%_50%,rgba(234,179,8,0.1),transparent_70%)]"
            ></div>

            <!-- Bordes brillantes -->
            <div
              class="absolute inset-0 border border-yellow-600/20 rounded-xl group-hover:border-yellow-500/40 transition-all duration-500"
            ></div>
            <div
              class="absolute inset-[1px] border border-yellow-600/10 rounded-xl group-hover:border-yellow-500/20 transition-all duration-500"
            ></div>

            <!-- Contenido -->
            <div class="relative flex items-start space-x-4">
              <div
                class="w-12 h-12 bg-gradient-to-br from-yellow-500 to-yellow-700 rounded-lg flex items-center justify-center flex-shrink-0 shadow-lg border border-yellow-600/50 transition-all duration-500 group-hover:shadow-yellow-500/20 group-hover:scale-110"
              >
                <component
                  :is="feature.icon"
                  class="transition-transform duration-500 group-hover:scale-110"
                />
              </div>
              <div class="flex-1">
                <h3
                  class="text-xl font-bold bg-gradient-to-r from-yellow-300 to-yellow-500 bg-clip-text text-transparent mb-2"
                  style="font-family: 'Cinzel', serif"
                >
                  {{ feature.title }}
                </h3>
                <p
                  class="text-yellow-200/90 leading-relaxed transition-all duration-500 group-hover:text-yellow-100"
                  style="font-family: 'Montserrat', sans-serif"
                >
                  {{ feature.description }}
                </p>
              </div>
            </div>

            <!-- Efecto de brillo en hover -->
            <div
              class="absolute -inset-x-1/2 -top-1/2 h-40 w-[200%] opacity-0 group-hover:opacity-10 transition-opacity duration-700"
            >
              <div
                class="absolute inset-0 rotate-12 bg-gradient-to-r from-transparent via-yellow-400 to-transparent blur-2xl"
              ></div>
            </div>
          </div>
        </div>

        <!-- Video/Imagen de características -->
        <div
          class="relative opacity-0"
          :class="{ 'slide-in-right': isIntersecting }"
          style="animation-delay: 0.6s"
        >
          <div class="relative rounded-lg overflow-hidden shadow-2xl">
            <img
              src="@/assets/Juego.jpeg"
              alt="Características del Juego"
              class="w-full h-auto object-cover"
            />
            <div class="absolute inset-0 bg-gradient-to-t from-black/50 to-transparent"></div>
          </div>

          <!-- Decoración adicional -->
          <div
            class="absolute -inset-0.5 bg-gradient-to-r from-yellow-500/20 to-yellow-600/20 blur-2xl opacity-50 -z-10"
          ></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { defineComponent, h } from 'vue'
import { useIntersectionObserver } from '@/composables/useIntersectionObserver'

// Componentes de iconos
const CombatIcon = defineComponent({
  render() {
    return h(
      'svg',
      {
        class: 'w-6 h-6 text-white',
        fill: 'none',
        stroke: 'currentColor',
        viewBox: '0 0 24 24',
      },
      [
        h('path', {
          'stroke-linecap': 'round',
          'stroke-linejoin': 'round',
          'stroke-width': '2',
          d: 'M13 10V3L4 14h7v7l9-11h-7z',
        }),
      ],
    )
  },
})

const WorldIcon = defineComponent({
  render() {
    return h(
      'svg',
      {
        class: 'w-6 h-6 text-white',
        fill: 'none',
        stroke: 'currentColor',
        viewBox: '0 0 24 24',
      },
      [
        h('path', {
          'stroke-linecap': 'round',
          'stroke-linejoin': 'round',
          'stroke-width': '2',
          d: 'M3.055 11H5a2 2 0 012 2v1a2 2 0 002 2 2 2 0 012 2v2.945M8 3.935V5.5A2.5 2.5 0 0010.5 8h.5a2 2 0 012 2 2 2 0 104 0 2 2 0 012-2h1.064M15 20.488V18a2 2 0 012-2h3.064',
        }),
      ],
    )
  },
})

const StoryIcon = defineComponent({
  render() {
    return h(
      'svg',
      {
        class: 'w-6 h-6 text-white',
        fill: 'none',
        stroke: 'currentColor',
        viewBox: '0 0 24 24',
      },
      [
        h('path', {
          'stroke-linecap': 'round',
          'stroke-linejoin': 'round',
          'stroke-width': '2',
          d: 'M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.746 0 3.332.477 4.5 1.253v13C19.832 18.477 18.246 18 16.5 18c-1.746 0-3.332.477-4.5 1.253',
        }),
      ],
    )
  },
})

// Datos de características
const features = [
  {
    title: 'Combate Épico',
    description: 'Sistema de combate fluido con combos devastadores y habilidades únicas.',
    icon: CombatIcon,
  },
  {
    title: 'Mundo Abierto',
    description: 'Explora vastos territorios llenos de secretos, mazmorras y criaturas místicas.',
    icon: WorldIcon,
  },
  {
    title: 'Historia Profunda',
    description: 'Una narrativa envolvente con múltiples finales y decisiones que importan.',
    icon: StoryIcon,
  },
]

const { isIntersecting, target: sectionRef } = useIntersectionObserver()
</script>

<style scoped>
.bg-clip-text {
  -webkit-background-clip: text;
  background-clip: text;
}

.particle-star {
  position: absolute;
  width: 2px;
  height: 2px;
  background: #ffd700;
  border-radius: 50%;
  animation: twinkle 5s infinite;
}

@keyframes twinkle {
  0%,
  100% {
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
}

.fade-in-up {
  animation: fadeInUp 1s ease-out forwards;
}

.slide-in-left {
  animation: slideInLeft 0.8s ease-out forwards;
}

.slide-in-right {
  animation: slideInRight 0.8s ease-out forwards;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideInLeft {
  from {
    opacity: 0;
    transform: translateX(-50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes slideInRight {
  from {
    opacity: 0;
    transform: translateX(50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}
</style>
