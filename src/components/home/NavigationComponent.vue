<template>
  <header class="relative">
    <!-- Barra de navegación -->
  <nav
      class="fixed top-0 w-full z-50 bg-black/90 backdrop-blur-sm border-b border-yellow-600 shadow-xl"
    >
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex items-center justify-between h-18">
          <!-- Logo -->
          <div class="flex items-center">
            <img
              src="@/assets/LogoUmbral.png"
              alt="Logo Umbral"
              class="h-26 w-auto drop-shadow-lg"
            />
          </div>

          <!-- Desktop Navigation -->
          <div class="hidden md:block">
            <div class="ml-10 flex items-baseline space-x-8">
              <a
                v-for="(item, index) in navItems"
                :key="index"
                :href="item.href"
                class="text-gray-200 hover:text-yellow-400 transition-colors font-semibold"
                :class="{ 'text-white font-bold': item.href === '#inicio' }"
              >
                {{ item.text }}
              </a>
            </div>
          </div>

          <!-- CTA Button -->
          <div class="hidden md:block">
            <button
              class="bg-gradient-to-r from-yellow-500 to-yellow-700 hover:from-yellow-600 hover:to-yellow-800 px-6 py-2 rounded-xl text-sm font-bold text-black shadow-lg transition-all border border-yellow-600"
            >
              COMPRAR AHORA
            </button>
          </div>

          <!-- Mobile menu button -->
          <div class="md:hidden">
            <button @click="isMenuOpen = !isMenuOpen" class="text-yellow-400 hover:text-white">
              <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M4 6h16M4 12h16M4 18h16"
                />
              </svg>
            </button>
          </div>
        </div>
      </div>
    </nav>

    <!-- Menú móvil -->
    <transition
      enter-active-class="transition ease-out duration-200"
      enter-from-class="opacity-0 -translate-y-1"
      enter-to-class="opacity-100 translate-y-0"
      leave-active-class="transition ease-in duration-150"
      leave-from-class="opacity-100 translate-y-0"
      leave-to-class="opacity-0 -translate-y-1"
    >
      <div
        v-if="isMenuOpen"
        class="md:hidden fixed top-[72px] left-0 right-0 z-40 bg-black/95 backdrop-blur-sm border-b border-yellow-600/30"
      >
        <div class="px-2 pt-2 pb-3 space-y-1">
          <a
            v-for="(item, index) in navItems"
            :key="index"
            :href="item.href"
            @click="isMenuOpen = false"
            class="block px-3 py-2 text-gray-300 hover:text-yellow-400 transition-colors"
            :class="{ 'text-white': item.href === '#inicio' }"
          >
            {{ item.text }}
          </a>
          <button
            @click="isMenuOpen = false"
            class="w-full text-left px-3 py-2 bg-gradient-to-r from-yellow-500 to-yellow-700 hover:from-yellow-600 hover:to-yellow-800 text-black font-bold rounded-xl mt-2 border border-yellow-600 transition-all"
          >
            COMPRAR AHORA
          </button>
        </div>
      </div>
    </transition>
  </header>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const isMenuOpen = ref(false)

const navItems = [
  { href: '#inicio', text: 'INICIO' },
  { href: '#informacion', text: 'INFORMACIÓN GENERAL' },
  { href: '#noticias', text: 'NOTICIAS' },
  { href: '#tienda', text: 'TIENDA' },
  { href: '#soporte', text: 'SOPORTE TÉCNICO' },
]
</script>
