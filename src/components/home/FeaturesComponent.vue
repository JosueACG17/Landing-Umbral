<template>
  <section
    id="caracteristicas"
    class="py-32 bg-black relative overflow-hidden"
    ref="sectionRef"
  >
    <!-- Simplified background effects -->
    <div class="absolute inset-0 bg-[radial-gradient(circle_at_30%_20%,rgba(234,179,8,0.05),transparent_50%)]"></div>
    <div class="absolute inset-0 bg-[radial-gradient(circle_at_70%_80%,rgba(234,179,8,0.05),transparent_50%)]"></div>

    <!-- Contenido principal -->
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <!-- Minimalist header with clean typography -->
      <div class="text-center mb-10 opacity-0" :class="{ 'fade-in-up': isIntersecting }">
        <p class="text-yellow-400 text-sm tracking-[0.3em] uppercase mb-4 font-light">
          CARACTERÍSTICAS DEL JUEGO
        </p>
        <h2
            class="text-5xl sm:text-7xl md:text-8xl lg:text-9xl font-black text-transparent bg-clip-text bg-gradient-to-b from-yellow-300 via-yellow-400 to-yellow-600 mb-4 tracking-tight leading-none fade-in"
            style="
              animation-delay: 0.1s;
              text-shadow: 0 0 40px rgba(234, 179, 8, 0.3);
              font-family: 'Cinzel', serif;
            "
          >
            MECÁNICAS
          </h2>
        <p class="text-gray-300 text-lg max-w-2xl mx-auto font-light leading-relaxed">
          Descubre las características que hacen de UMBRAL una experiencia única
        </p>
      </div>

      <!-- New grid layout with large feature cards -->
      <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
        <div
          v-for="(feature, index) in features"
          :key="index"
          class="group relative overflow-hidden bg-zinc-950 border border-zinc-900 hover:border-yellow-500/30 transition-all duration-700 opacity-0"
          :class="{ 'slide-in-up': isIntersecting }"
          :style="{ 'animation-delay': `${0.15 * (index + 1)}s` }"
        >
          <!-- Large icon area with glow effect -->
          <div class="relative h-80 overflow-hidden">
            <div class="absolute inset-0 bg-gradient-to-b from-zinc-900 to-black"></div>
            <div class="absolute inset-0 flex items-center justify-center">
              <div
                class="w-24 h-24 rounded-full bg-yellow-500/10 flex items-center justify-center backdrop-blur-sm border border-yellow-500/20 group-hover:scale-110 group-hover:bg-yellow-500/20 transition-all duration-700"
              >
                <component
                  :is="feature.icon"
                  class="transition-all duration-700 group-hover:scale-110"
                />
              </div>
            </div>
            <!-- Subtle hover glow -->
            <div
              class="absolute inset-0 bg-gradient-to-t from-yellow-500/0 via-yellow-500/0 to-yellow-500/0 group-hover:from-yellow-500/5 group-hover:via-yellow-500/0 transition-all duration-700"
            ></div>
          </div>

          <!-- Clean content area -->
          <div class="p-8 pt-6">
            <h3
              class="text-2xl font-bold text-white mb-4 group-hover:text-yellow-400 transition-colors duration-500"
              style="font-family: 'Cinzel', serif"
            >
              {{ feature.title }}
            </h3>
            <p class="text-gray-400 leading-relaxed font-light">
              {{ feature.description }}
            </p>
          </div>

          <!-- Minimal accent line -->
          <div
            class="absolute bottom-0 left-0 h-[2px] w-0 bg-gradient-to-r from-yellow-500 to-yellow-600 group-hover:w-full transition-all duration-700"
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
          d: 'M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 16.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.746 0 3.332.477 4.5 1.253v13C19.832 18.477 18.246 18 16.5 18c-1.746 0-3.332.477-4.5 1.253',
        }),
      ],
    )
  },
})

// Datos de características
const features = [
  {
    title: 'Combate Épico',
    description: 'Sistema de combate fluido con combos devastadores y habilidades únicas para cada campeón.',
    icon: CombatIcon,
  },
  {
    title: 'Mundo Abierto',
    description: 'Explora vastos territorios llenos de secretos, mazmorras y criaturas místicas que aguardan.',
    icon: WorldIcon,
  },
  {
    title: 'Historia Profunda',
    description: 'Una narrativa envolvente con múltiples finales y decisiones que moldearán tu destino.',
    icon: StoryIcon,
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
</style>
