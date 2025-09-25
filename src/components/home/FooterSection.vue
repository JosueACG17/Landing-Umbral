<template>
  <footer
    class="bg-gradient-to-t from-black via-gray-950 to-black border-t border-gray-800 py-12 fade-in"
    style="animation-delay: 0.2s"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <slot />
      <div class="border-t border-gray-800 mt-8 pt-8 text-center">
        <p class="text-yellow-300 tracking-wide text-sm">
          &copy; 2025 <span class="text-yellow-400 font-bold">UMBRAL</span>. Todos los derechos
          reservados.
        </p>
      </div>
    </div>
  </footer>
</template>
