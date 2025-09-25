<template>
  <div class="relative w-full py-16 overflow-hidden">
    <!-- Fondo con efecto de niebla -->
    <div class="absolute inset-0 bg-black/50 backdrop-blur-sm"></div>
    <div class="absolute inset-0 bg-gradient-to-r from-black via-transparent to-black"></div>

    <!-- Contenido -->
    <div class="relative z-10 flex flex-col items-center">
      <!-- Decoración superior -->
      <div class="flex items-center w-full max-w-4xl mx-auto mb-8">
        <div
          class="flex-1 h-[1px] bg-gradient-to-r from-transparent via-yellow-500 to-transparent"
        ></div>
        <div class="px-4">
          <svg
            class="w-8 h-8 text-yellow-400"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z"
            />
          </svg>
        </div>
        <div
          class="flex-1 h-[1px] bg-gradient-to-l from-transparent via-yellow-500 to-transparent"
        ></div>
      </div>

      <!-- Título principal -->
      <h2
        class="text-3xl sm:text-4xl lg:text-5xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-yellow-300 to-yellow-500 mb-4 px-4"
        style="font-family: 'Cinzel', serif"
      >
        ¡Bienvenido a UMBRAL!
      </h2>

      <!-- Texto descriptivo -->
      <p
        class="text-lg sm:text-xl text-yellow-200/90 text-center max-w-2xl mx-auto px-4 sm:px-6 leading-relaxed"
        style="font-family: 'Montserrat', sans-serif"
      >
        Prepárate para una experiencia épica en un mundo de fantasía oscura donde cada decisión
        forja tu destino y cada batalla define tu legado.
      </p>

      <!-- Decoración inferior -->
      <div class="flex items-center w-full max-w-4xl mx-auto mt-8">
        <div
          class="flex-1 h-[1px] bg-gradient-to-r from-transparent via-yellow-500 to-transparent"
        ></div>
        <div class="px-4">
          <svg
            class="w-8 h-8 text-yellow-400 transform rotate-180"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z"
            />
          </svg>
        </div>
        <div
          class="flex-1 h-[1px] bg-gradient-to-l from-transparent via-yellow-500 to-transparent"
        ></div>
      </div>
    </div>

    <!-- Efecto de partículas lateral -->
    <div
      class="absolute inset-y-0 left-0 w-32 bg-gradient-to-r from-yellow-500/5 to-transparent"
    ></div>
    <div
      class="absolute inset-y-0 right-0 w-32 bg-gradient-to-l from-yellow-500/5 to-transparent"
    ></div>
  </div>
</template>

<style scoped>
.bg-clip-text {
  -webkit-background-clip: text;
  background-clip: text;
}
</style>
