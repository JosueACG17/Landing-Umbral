<template>
  <section
    id="noticias"
    class="py-20 bg-gradient-to-b from-gray-900 to-black relative overflow-hidden"
  >
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
      <div class="text-center mb-16 opacity-0 fade-in-up" ref="titleRef">
        <div class="flex items-center justify-center mb-4 space-x-4">
          <div
            class="h-[1px] w-20 bg-gradient-to-r from-transparent via-yellow-500 to-transparent"
          ></div>
          <h2
            class="text-4xl sm:text-5xl font-bold bg-gradient-to-r from-yellow-300 to-yellow-500 bg-clip-text text-transparent"
            style="font-family: 'Cinzel', serif"
          >
            NOTICIAS
          </h2>
          <div
            class="h-[1px] w-20 bg-gradient-to-l from-transparent via-yellow-500 to-transparent"
          ></div>
        </div>
        <p class="text-xl text-yellow-200/90 mt-4" style="font-family: 'Montserrat', sans-serif">
          Mantente al día con las últimas actualizaciones
        </p>
      </div>

      <!-- Grid de noticias -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <article
          v-for="(news, index) in newsItems"
          :key="index"
          class="group relative bg-black/70 backdrop-blur-md rounded-xl overflow-hidden transition-all duration-500 hover:scale-[1.02] opacity-0 fade-in"
          :style="{ animationDelay: `${0.2 * (index + 1)}s` }"
        >
          <!-- Bordes con brillo -->
          <div
            class="absolute inset-0 border border-yellow-600/20 rounded-xl group-hover:border-yellow-500/40 transition-all duration-500"
          ></div>
          <div
            class="absolute inset-[1px] border border-yellow-600/10 rounded-xl group-hover:border-yellow-500/20 transition-all duration-500"
          ></div>

          <!-- Imagen con overlay -->
          <div class="relative overflow-hidden h-48">
            <img
              :src="news.img"
              :alt="news.title"
              class="w-full h-full object-cover transition-all duration-700 group-hover:scale-110"
            />
            <!-- Overlay gradiente -->
            <div
              class="absolute inset-0 bg-gradient-to-t from-black via-black/50 to-transparent opacity-60 group-hover:opacity-40 transition-opacity duration-500"
            ></div>

            <!-- Fecha con efecto especial -->
            <div
              class="absolute top-4 right-4 px-3 py-1 bg-black/60 backdrop-blur-sm border border-yellow-500/30 rounded-full"
            >
              <span
                class="text-yellow-400 text-sm font-semibold tracking-wider"
                style="font-family: 'Montserrat', sans-serif"
                >{{ news.date }}</span
              >
            </div>
          </div>

          <!-- Contenido -->
          <div class="relative p-6 bg-gradient-to-b from-black/90 to-black/70">
            <h3
              class="text-xl font-bold bg-gradient-to-r from-yellow-300 to-yellow-500 bg-clip-text text-transparent mb-3 group-hover:from-yellow-400 group-hover:to-yellow-600 transition-all duration-500"
              style="font-family: 'Cinzel', serif"
            >
              {{ news.title }}
            </h3>
            <p
              class="text-yellow-200/90 text-sm leading-relaxed group-hover:text-yellow-100 transition-colors duration-500"
              style="font-family: 'Montserrat', sans-serif"
            >
              {{ news.description }}
            </p>

            <!-- Botón "Leer más" -->
            <div
              class="mt-4 flex items-center text-yellow-500 text-sm font-semibold transition-all duration-300 group-hover:text-yellow-400"
            >
              <span style="font-family: 'Montserrat', sans-serif">Leer más</span>
              <svg
                class="w-4 h-4 ml-2 transform transition-transform duration-300 group-hover:translate-x-1"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 5l7 7-7 7"
                />
              </svg>
            </div>
          </div>

          <!-- Efecto de brillo en hover -->
          <div
            class="absolute -inset-x-1/2 top-0 h-[200%] w-[200%] opacity-0 group-hover:opacity-10 transition-opacity duration-700"
          >
            <div
              class="absolute inset-0 rotate-12 bg-gradient-to-r from-transparent via-yellow-400 to-transparent blur-2xl"
            ></div>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { useIntersectionObserver } from '@/composables/useIntersectionObserver'

const { target: titleRef } = useIntersectionObserver()

const newsItems = [
  {
    title: 'Nuevo Sistema de Combate',
    description:
      'Descubre las mejoras en el sistema de combate que harán las batallas más épicas y dinámicas.',
    img: 'https://images.unsplash.com/photo-1465101046530-73398c7f28ca?auto=format&fit=crop&w=600&q=80',
    date: '25 Sep 2025',
  },
  {
    title: 'Exploración Expandida',
    description: 'Nuevas áreas por descubrir y secretos por encontrar en la próxima actualización.',
    img: 'https://images.unsplash.com/photo-1465101046530-73398c7f28ca?auto=format&fit=crop&w=600&q=80',
    date: '24 Sep 2025',
  },
  {
    title: 'Evento Especial',
    description:
      'Prepárate para un evento único que cambiará el destino de tu personaje para siempre.',
    img: 'https://images.unsplash.com/photo-1465101046530-73398c7f28ca?auto=format&fit=crop&w=600&q=80',
    date: '23 Sep 2025',
  },
]
</script>

<style scoped>
.bg-clip-text {
  -webkit-background-clip: text;
  background-clip: text;
}

.fade-in-up {
  animation: fadeInUp 1s ease-out forwards;
}

.fade-in {
  animation: fadeIn 1s ease-out forwards;
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

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>
