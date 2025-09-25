<template>
  <section id="inicio" class="relative h-screen mt-10 overflow-hidden">
    <!-- Fondo con efecto parallax -->
    <div class="absolute inset-0 z-0">
      <div class="relative w-full h-full">
        <img
          src="@/assets/Fondo_Hero.jpg"
          alt="Gothic Castle Interior"
          class="w-full h-full object-cover scale-110 brightness-75 transform transition-transform duration-[3s] hover:scale-105"
        />
        <!-- Overlays para profundidad -->
        <div class="absolute inset-0 bg-gradient-to-b from-black/90 via-black/40 to-black/40"></div>

        <!-- Efecto de patrón de rejilla -->
        <div class="absolute inset-0 bg-grid-pattern opacity-10"></div>

        <!-- Partículas flotantes -->
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
          </div>
        </div>
      </div>
    </div>

    <!-- Contenido principal -->
    <div class="relative z-10 h-full flex items-center">
      <div class="container mx-auto flex flex-col justify-center items-center text-center px-4">
        <!-- Título principal -->
        <div class="space-y-6 max-w-4xl">
          <h1
            class="text-6xl sm:text-7xl md:text-8xl lg:text-9xl font-black text-transparent bg-clip-text bg-gradient-to-b from-yellow-300 via-yellow-400 to-yellow-600 mb-4 tracking-tight leading-none fade-in"
            style="
              animation-delay: 0.1s;
              text-shadow: 0 0 40px rgba(234, 179, 8, 0.3);
              font-family: 'Cinzel', serif;
            "
          >
            UMBRAL
          </h1>

          <p
            class="text-2xl sm:text-3xl md:text-4xl text-yellow-200 font-light tracking-wider mb-2 slide-up opacity-0"
            style="
              animation-delay: 0.3s;
              letter-spacing: 0.2em;
              font-family: 'Montserrat', sans-serif;
            "
          >
            La forja de las almas
          </p>

          <!-- Separador decorativo -->
          <div
            class="w-24 h-0.5 mx-auto bg-gradient-to-r from-transparent via-yellow-500 to-transparent fade-in"
            style="animation-delay: 0.4s"
          ></div>

          <p
            class="text-xl sm:text-2xl md:text-3xl text-yellow-300/90 font-medium mt-6 max-w-2xl mx-auto leading-relaxed fade-in px-4"
            style="animation-delay: 0.5s; font-family: 'Montserrat', sans-serif"
          >
            Forja tu destino en el Reino de las Sombras
          </p>
        </div>

        <!-- Botones y plataformas -->
        <div class="mt-12 space-y-8">
          <!-- Botones principales -->
          <div class="flex flex-col md:flex-row items-center justify-center gap-6">
            <button
              class="cursor-pointer group relative px-12 py-5 w-64 overflow-hidden rounded-xl bg-gradient-to-br from-yellow-400 to-yellow-600 text-black font-bold text-lg transition-all duration-300 hover:scale-105 hover:shadow-2xl hover:shadow-yellow-600/20"
              style="animation-delay: 0.7s; font-family: 'Montserrat', sans-serif"
            >
              <span class="relative z-10">COMPRAR AHORA</span>
              <div
                class="absolute inset-0 z-0 bg-gradient-to-r from-yellow-300 to-yellow-500 opacity-0 group-hover:opacity-100 transition-opacity duration-300"
              ></div>
            </button>

            <button
              class="cursor-pointer group relative px-12 py-5 w-64 overflow-hidden rounded-xl bg-black/30 backdrop-blur-sm border-2 border-yellow-500/30 text-yellow-400 font-bold text-lg transition-all duration-300 hover:scale-105 hover:border-yellow-400 hover:shadow-2xl hover:shadow-yellow-600/20"
              style="animation-delay: 0.8s; font-family: 'Montserrat', sans-serif"
            >
              <span class="relative z-10">MIRA EL TRAILER</span>
              <div
                class="absolute inset-0 z-0 bg-gradient-to-r from-yellow-900/20 to-yellow-800/20 opacity-0 group-hover:opacity-100 transition-opacity duration-300"
              ></div>
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.bg-grid-pattern {
  background-image:
    linear-gradient(rgba(255, 215, 0, 0.1) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 215, 0, 0.1) 1px, transparent 1px);
  background-size: 20px 20px;
}

/* Partículas flotantes */
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
  animation: float 15s infinite;
  opacity: 0;
}

.particle:nth-child(1) {
  left: 10%;
  animation-delay: 0s;
}
.particle:nth-child(2) {
  left: 20%;
  animation-delay: 2s;
}
.particle:nth-child(3) {
  left: 35%;
  animation-delay: 4s;
}
.particle:nth-child(4) {
  left: 50%;
  animation-delay: 6s;
}
.particle:nth-child(5) {
  left: 65%;
  animation-delay: 8s;
}
.particle:nth-child(6) {
  left: 75%;
  animation-delay: 10s;
}
.particle:nth-child(7) {
  left: 85%;
  animation-delay: 12s;
}
.particle:nth-child(8) {
  left: 90%;
  animation-delay: 14s;
}
.particle:nth-child(9) {
  left: 95%;
  animation-delay: 16s;
}
.particle:nth-child(10) {
  left: 15%;
  animation-delay: 18s;
}

@keyframes float {
  0% {
    transform: translateY(100vh) scale(0);
    opacity: 0;
  }
  20% {
    opacity: 0.5;
  }
  50% {
    opacity: 0.8;
  }
  80% {
    opacity: 0.5;
  }
  100% {
    transform: translateY(-100px) scale(1);
    opacity: 0;
  }
}

/* Mejoras en animaciones */
.fade-in {
  animation: enhancedFadeIn 1.2s cubic-bezier(0.4, 0, 0.2, 1) forwards;
}

@keyframes enhancedFadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
