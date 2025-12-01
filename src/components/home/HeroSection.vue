<template>
  <section
    id="inicio"
    class="relative min-h-screen overflow-hidden flex items-center bg-black pt-20 lg:pt-0"
  >
    <!-- Fondo con efectos sutiles -->
    <div class="absolute inset-0 z-0">

      <!-- Grid sutil -->
      <div class="absolute inset-0 bg-grid-pattern opacity-[0.03]"></div>

      <!-- Glow effects sutiles en esquinas -->
      <div
        class="absolute top-0 right-0 w-[500px] h-[500px] bg-yellow-500/10 rounded-full filter blur-[150px] animate-pulse-slow"
      ></div>
      <div
        class="absolute bottom-0 left-0 w-[500px] h-[500px] bg-orange-500/10 rounded-full filter blur-[150px] animate-pulse-slow"
        style="animation-delay: 2s"
      ></div>
    </div>

    <!-- Contenido -->
    <div class="relative z-10 w-full">
      <div class="container mx-auto px-4 sm:px-6 lg:px-12 xl:px-16">
        <div
          class="grid grid-cols-1 lg:grid-cols-12 gap-8 lg:gap-12 items-center min-h-screen py-16 sm:py-20"
        >
          <!-- Columna Izquierda - Contenido (7 columnas) -->
          <div
            class="lg:col-span-7 flex flex-col justify-center space-y-8 lg:space-y-10 order-1 lg:order-1"
          >
            <!-- Título principal -->
            <div class="space-y-4 lg:space-y-6">
              <h1
                class="text-4xl sm:text-5xl md:text-6xl lg:text-7xl xl:text-8xl font-black text-white leading-[1.1] fade-in"
                style="animation-delay: 0.2s; font-family: 'Cinzel', serif"
              >
                Bienvenido a
                <span
                  class="block text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 via-yellow-500 to-orange-500 mt-2"
                >
                  UMBRAL
                </span>
              </h1>

              <p
                class="text-lg sm:text-xl lg:text-2xl text-gray-400 max-w-2xl leading-relaxed fade-in"
                style="animation-delay: 0.3s; font-family: 'Inter', sans-serif"
              >
                Forja tu destino en el Reino de las Sombras. Elige tu cazador, domina tu rol y
                conquista el campo de batalla.
              </p>
            </div>

            <!-- CTAs -->
            <div class="flex flex-col sm:flex-row gap-4 fade-in" style="animation-delay: 0.4s">
              <a
                href="#campeones"
                class="group relative inline-flex items-center justify-center gap-3 px-8 py-4 bg-gradient-to-r from-yellow-500 to-orange-500 text-black font-bold text-base rounded-xl overflow-hidden transition-all duration-300 hover:scale-[1.02] hover:shadow-2xl hover:shadow-yellow-500/25 cursor-pointer"
                style="font-family: 'Inter', sans-serif"
              >
                <svg
                  class="w-5 h-5 group-hover:rotate-12 transition-transform"
                  fill="currentColor"
                  viewBox="0 0 20 20"
                >
                  <path
                    d="M10.394 2.08a1 1 0 00-.788 0l-7 3a1 1 0 000 1.84L5.25 8.051a.999.999 0 01.356-.257l4-1.714a1 1 0 11.788 1.838L7.667 9.088l1.94.831a1 1 0 00.787 0l7-3a1 1 0 000-1.838l-7-3zM3.31 9.397L5 10.12v4.102a8.969 8.969 0 00-1.05-.174 1 1 0 01-.89-.89 11.115 11.115 0 01.25-3.762zM9.3 16.573A9.026 9.026 0 007 14.935v-3.957l1.818.78a3 3 0 002.364 0l5.508-2.361a11.026 11.026 0 01.25 3.762 1 1 0 01-.89.89 8.968 8.968 0 00-5.35 2.524 1 1 0 01-1.4 0zM6 18a1 1 0 001-1v-2.065a8.935 8.935 0 00-2-.712V17a1 1 0 001 1z"
                  />
                </svg>
                <span>Explorar Personajes</span>
                <div
                  class="absolute inset-0 bg-white/20 transform scale-x-0 group-hover:scale-x-100 transition-transform origin-left duration-300"
                ></div>
              </a>

              <a
                href="#app-movil"
                class="group inline-flex items-center justify-center gap-3 px-8 py-4 bg-white/5 backdrop-blur-sm text-white font-bold text-base rounded-xl border border-white/10 overflow-hidden transition-all duration-300 hover:bg-white/10 hover:border-white/20 cursor-pointer"
                style="font-family: 'Inter', sans-serif"
              >
                <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20">
                  <path
                    d="M2 6a2 2 0 012-2h6a2 2 0 012 2v8a2 2 0 01-2 2H4a2 2 0 01-2-2V6zM14.553 7.106A1 1 0 0014 8v4a1 1 0 00.553.894l2 1A1 1 0 0018 13V7a1 1 0 00-1.447-.894l-2 1z"
                  />
                </svg>
                <span>Ver App Móvil</span>
              </a>
            </div>

            <!-- Stats minimalistas -->
            <div
              class="grid grid-cols-3 gap-8 pt-8 border-t border-white/5 fade-in"
              style="animation-delay: 0.5s"
            >
              <div class="group cursor-default">
                <div
                  class="text-4xl font-bold text-yellow-400 mb-1 group-hover:scale-110 transition-transform"
                  style="font-family: 'Cinzel', serif"
                >
                  4
                </div>
                <div class="text-sm text-gray-500 uppercase tracking-wider">Personajes</div>
              </div>

              <div class="group cursor-default">
                <div
                  class="text-4xl font-bold text-yellow-400 mb-1 group-hover:scale-110 transition-transform"
                  style="font-family: 'Cinzel', serif"
                >
                  4
                </div>
                <div class="text-sm text-gray-500 uppercase tracking-wider">Roles únicos</div>
              </div>

              <div class="group cursor-default">
                <div
                  class="text-4xl font-bold text-orange-400 mb-1 group-hover:scale-110 transition-transform"
                  style="font-family: 'Cinzel', serif"
                >
                  ∞
                </div>
                <div class="text-sm text-gray-500 uppercase tracking-wider">Batallas</div>
              </div>
            </div>
          </div>

          <!-- Columna Derecha - Visual Hero (5 columnas) -->
          <div
            class="lg:col-span-5 relative order-2 lg:order-2 fade-in mb-12 lg:mb-0"
            style="animation-delay: 0.3s"
          >
            <div
              class="relative aspect-square max-w-[400px] sm:max-w-[450px] lg:max-w-[550px] mx-auto lg:ml-auto"
            >
              <!-- Círculo de fondo con gradiente -->
              <div
                class="absolute inset-0 rounded-full bg-gradient-to-br from-yellow-500/20 via-orange-500/10 to-transparent filter blur-3xl"
              ></div>

              <!-- Anillo decorativo principal -->
              <div class="absolute inset-0 rounded-full border border-yellow-500/20"></div>
              <div
                class="absolute inset-4 rounded-full border border-yellow-500/10 animate-spin-very-slow"
              ></div>

              <!-- Contenedor de imagen -->
              <div class="relative w-full h-full p-8">
                <div
                  class="relative w-full h-full rounded-full overflow-hidden border-2 border-yellow-500/20 shadow-2xl shadow-yellow-500/20 bg-gradient-to-br from-gray-900 to-black group hover:scale-105 transition-all duration-700"
                >
                  <!-- Placeholder -->
                  <div class="w-full h-full flex items-center justify-center relative">
                    <img
                      src="/Fondo_Hero.png"
                      alt="Hero Character"
                      class="w-full h-full object-cover"
                    />
                    </div>


                    <!-- Efectos de luz sutiles -->
                    <div
                      class="absolute top-1/4 right-1/4 w-32 h-32 bg-yellow-500/10 rounded-full filter blur-3xl"
                    ></div>
                    <div
                      class="absolute bottom-1/4 left-1/4 w-32 h-32 bg-orange-500/10 rounded-full filter blur-3xl"
                    ></div>
                  </div>

                  <!-- Overlay -->
                  <div
                    class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent pointer-events-none"
                  ></div>

                  <!-- Partículas sutiles -->
                  <div
                    class="absolute top-[15%] right-[20%] w-2 h-2 bg-yellow-400 rounded-full animate-ping opacity-40"
                  ></div>
                  <div
                    class="absolute bottom-[25%] left-[15%] w-1.5 h-1.5 bg-orange-400 rounded-full animate-ping opacity-40"
                    style="animation-delay: 1s"
                  ></div>
                  <div
                    class="absolute top-[60%] right-[15%] w-1.5 h-1.5 bg-yellow-300 rounded-full animate-ping opacity-40"
                    style="animation-delay: 2s"
                  ></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

    <!-- Scroll indicator elegante -->
    <div
      class="absolute bottom-8 left-1/2 transform -translate-x-1/2 z-20 animate-bounce hidden lg:flex"
    >
      <a
        href="#campeones"
        class="flex flex-col items-center gap-2 text-gray-600 hover:text-yellow-400 transition-colors cursor-pointer group"
      >
        <span class="text-xs uppercase tracking-widest font-medium">Explorar</span>
        <div
          class="w-6 h-10 rounded-full border-2 border-gray-700 group-hover:border-yellow-500/50 flex items-start justify-center p-2 transition-colors"
        >
          <div
            class="w-1 h-2 bg-gray-600 group-hover:bg-yellow-400 rounded-full animate-bounce transition-colors"
          ></div>
        </div>
      </a>
    </div>
  </section>
</template>

<style scoped>
.bg-grid-pattern {
  background-image:
    linear-gradient(rgba(255, 255, 255, 0.02) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.02) 1px, transparent 1px);
  background-size: 80px 80px;
}

/* Pulse muy sutil */
@keyframes pulse-slow {
  0%,
  100% {
    opacity: 0.5;
  }
  50% {
    opacity: 0.8;
  }
}

.animate-pulse-slow {
  animation: pulse-slow 6s ease-in-out infinite;
}

/* Rotación ultra lenta */
@keyframes spin-very-slow {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

.animate-spin-very-slow {
  animation: spin-very-slow 60s linear infinite;
}

/* Float sutil */
@keyframes float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-15px);
  }
}

.animate-float {
  animation: float 4s ease-in-out infinite;
}

/* Fade in suave */
.fade-in {
  animation: fadeInUp 0.8s ease forwards;
  opacity: 0;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(15px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
