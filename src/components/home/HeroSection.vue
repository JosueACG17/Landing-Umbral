<template>
  <section id="inicio" class="relative min-h-screen overflow-hidden flex items-center">
    <!-- Fondo con parallax -->
    <div class="absolute inset-0 z-0">
      <div class="relative w-full h-full">
        <img
          src="../../../public/Fondo_Hero.jpg"
          alt="Gothic Castle Interior"
          class="w-full h-full object-cover object-center scale-110 brightness-75 transform transition-transform duration-[3s] hover:scale-105"
        />

        <!-- Overlays -->
        <div class="absolute inset-0 bg-gradient-to-b from-black/60 via-black/50 to-black/80"></div>
        <div class="absolute inset-0 bg-grid-pattern opacity-10"></div>

        <!-- Partículas -->
        <div class="absolute inset-0 overflow-hidden pointer-events-none">
          <div class="particles-container">
            <div class="particle"></div>
            <div class="particle"></div>
            <div class="particle"></div>
            <div class="particle"></div>
            <div class="particle"></div>
            <div class="particle"></div>
            <div class="particle"></div>
            <div class="particle"></div>
            <div class="particle"></div>
            <div class="particle"></div>
            <div class="particle"></div>
          </div>
        </div>
      </div>
    </div>

    <!-- Contenido -->
    <div class="relative z-10 w-full flex items-center">
      <div class="container mx-auto flex flex-col justify-center items-center text-center px-4">

        <!-- Título -->
        <div class="space-y-4 sm:space-y-6 max-w-4xl">
          <h1
            class="text-5xl sm:text-6xl md:text-7xl lg:text-8xl xl:text-9xl font-black text-transparent bg-clip-text bg-gradient-to-b from-yellow-300 via-yellow-400 to-yellow-600 tracking-tight fade-in"
            style="animation-delay: 0.1s; text-shadow: 0 0 40px rgba(234, 179, 8, 0.3); font-family: 'Cinzel', serif;"
          >
            UMBRAL
          </h1>

          <p
            class="text-xl sm:text-2xl md:text-3xl lg:text-4xl text-yellow-200 font-light tracking-wider slide-up opacity-0"
            style="animation-delay: 0.3s; letter-spacing: 0.2em; font-family: 'Montserrat', sans-serif;"
          >
            La forja de las almas
          </p>

          <!-- Línea decorativa -->
          <div
            class="w-20 sm:w-28 h-0.5 mx-auto bg-gradient-to-r from-transparent via-yellow-500 to-transparent fade-in"
            style="animation-delay: 0.4s"
          ></div>

          <p
            class="text-base sm:text-lg md:text-xl lg:text-2xl text-yellow-300/90 font-medium mt-4 max-w-xl sm:max-w-2xl mx-auto leading-relaxed fade-in"
            style="animation-delay: 0.5s; font-family: 'Montserrat', sans-serif"
          >
            Forja tu destino en el Reino de las Sombras
          </p>
        </div>

        <!-- Stats y botones -->
        <div class="mt-10 sm:mt-12 space-y-8">

          <!-- Estadísticas -->
          <div class="flex flex-wrap items-center justify-center gap-6 sm:gap-10 fade-in" style="animation-delay: 0.6s">
            <div class="text-center">
              <div class="text-3xl sm:text-4xl font-bold text-yellow-400" style="font-family: 'Cinzel', serif">
                {{ championCount }}
              </div>
              <div class="text-xs sm:text-sm text-yellow-200/80 uppercase tracking-wider">Reyes</div>
            </div>

            <div class="hidden sm:block h-12 w-px bg-yellow-500/30"></div>

            <div class="text-center">
              <div class="text-3xl sm:text-4xl font-bold text-yellow-400" style="font-family: 'Cinzel', serif">
                {{ roleCount }}
              </div>
              <div class="text-xs sm:text-sm text-yellow-200/80 uppercase tracking-wider">Roles</div>
            </div>

            <div class="hidden sm:block h-12 w-px bg-yellow-500/30"></div>

            <div class="text-center">
              <div class="text-3xl sm:text-4xl font-bold text-orange-400" style="font-family: 'Cinzel', serif">1</div>
              <div class="text-xs sm:text-sm text-orange-200/80 uppercase tracking-wider">Jefe Final</div>
            </div>

            <div class="hidden sm:block h-12 w-px bg-yellow-500/30"></div>

            <div class="text-center">
              <div class="text-3xl sm:text-4xl font-bold text-orange-400" style="font-family: 'Cinzel', serif">∞</div>
              <div class="text-xs sm:text-sm text-orange-200/80 uppercase tracking-wider">Súbditos</div>
            </div>
          </div>

          <!-- Botones -->
          <div class="flex flex-col md:flex-row items-center justify-center gap-5">
            <a
              href="#campeones"
              class="cursor-pointer group relative px-10 py-4 sm:px-12 sm:py-5 w-56 sm:w-64 overflow-hidden rounded-xl bg-gradient-to-br from-yellow-400 to-yellow-600 text-black font-bold text-lg transition-all duration-300 hover:scale-105 hover:shadow-2xl hover:shadow-yellow-600/50 fade-in"
              style="animation-delay: 0.7s; font-family: 'Montserrat', sans-serif"
            >
              <span class="relative z-10">VER REYES</span>
              <div class="absolute inset-0 z-0 bg-gradient-to-r from-yellow-300 to-yellow-500 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
            </a>

            <a
              href="#app-movil"
              class="cursor-pointer group relative px-10 py-4 sm:px-12 sm:py-5 w-56 sm:w-64 overflow-hidden rounded-xl bg-black/40 backdrop-blur-sm border border-yellow-500/40 text-yellow-400 font-bold text-lg transition-all duration-300 hover:scale-105 hover:border-yellow-400 hover:shadow-2xl hover:shadow-yellow-600/50 fade-in"
              style="animation-delay: 0.8s; font-family: 'Montserrat', sans-serif"
            >
              <span class="relative z-10">VER APP MÓVIL</span>
              <div class="absolute inset-0 z-0 bg-gradient-to-r from-yellow-900/20 to-yellow-800/20 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
            </a>
          </div>

        </div>
      </div>
    </div>
  </section>
</template>
<script setup lang="ts">
import { ref } from 'vue'

const championCount = ref(4)
const roleCount = ref(4)
</script>
<style scoped>
.bg-grid-pattern {
  background-image:
    linear-gradient(rgba(255, 215, 0, 0.08) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 215, 0, 0.08) 1px, transparent 1px);
  background-size: 22px 22px;
}

/* Partículas */
.particles-container {
  width: 100%;
  height: 100%;
  position: relative;
}

.particle {
  position: absolute;
  width: 3px;
  height: 3px;
  background: rgba(255, 215, 0, 0.6);
  border-radius: 50%;
  pointer-events: none;
  animation: float 14s infinite linear;
  opacity: 0;
}

.particle:nth-child(n) {
  left: calc(10% * var(--i));
  animation-delay: calc(1.4s * var(--i));
}

@keyframes float {
  0% {
    transform: translateY(110vh) scale(0);
    opacity: 0;
  }
  20% {
    opacity: 0.5;
  }
  55% {
    opacity: 0.9;
  }
  100% {
    transform: translateY(-120px) scale(1);
    opacity: 0;
  }
}

/* Animaciones */
.fade-in {
  animation: fadeInUp 1.2s ease forwards;
  opacity: 0;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(14px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

</style>
