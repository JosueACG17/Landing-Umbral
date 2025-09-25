<template>
  <section
    id="personajes"
    class="py-20 bg-gradient-to-b from-black via-gray-950 to-gray-900 flex justify-center items-center overflow-hidden"
  >
    <div
      class="w-full max-w-7xl flex flex-col md:flex-row items-center md:items-stretch gap-8 px-4 sm:px-6 lg:px-8 relative z-10"
    >
      <!-- Selección y texto -->
      <div
        class="flex-1 flex flex-col justify-center items-center md:items-start text-center md:text-left fade-in"
        style="animation-delay: 0.1s"
      >
        <h3 class="text-lg text-gray-200 mb-2 tracking-widest uppercase">ELIGE TU</h3>
        <h2
          class="text-5xl sm:text-6xl font-extrabold text-yellow-400 mb-4 drop-shadow"
          style="
            font-family:
              'Oswald',
              Impact,
              Arial Black,
              sans-serif;
            letter-spacing: 0.03em;
          "
        >
          <span class="text-yellow-500 animate-pulse">CAMPEÓN</span>
        </h2>
        <p
          class="text-base sm:text-lg text-gray-300 mb-6 max-w-md slide-up"
          style="animation-delay: 0.2s"
        >
          Ya sea que prefieras lanzarte directo a la batalla, apoyar a tus compañeros de equipo, o
          algo intermedio, hay un lugar para ti en el Reino.
        </p>
        <div class="flex flex-row gap-4 mb-8">
          <button
            class="px-8 py-3 cursor-pointer bg-gradient-to-r from-yellow-500 to-yellow-700 hover:from-yellow-600 hover:to-yellow-800 hover:text-white text-black font-bold rounded-xl shadow-lg card-hover border border-yellow-600 transition-all"
          >
            DESCUBRIR MÁS CAMPEONES
          </button>
          <button
            class="px-8 py-3 cursor-pointer bg-gradient-to-r from-yellow-700 to-yellow-500 hover:from-yellow-800 hover:to-yellow-600 hover:text-white text-black font-bold rounded-xl shadow-lg card-hover border border-yellow-600 transition-all"
          >
            JUEGA AHORA
          </button>
        </div>
        <div class="flex flex-row flex-wrap gap-8 justify-center md:justify-start mt-8">
          <button
            v-for="(role, idx) in roles"
            :key="role.name"
            @click="selectedIdx = idx"
            class="flex flex-col items-center group focus:outline-none"
          >
            <component
              :is="role.icon"
              :class="[
                'mb-2 transition-all cursor-pointer',
                selectedIdx === idx
                  ? 'scale-125 drop-shadow-lg'
                  : 'opacity-60 group-hover:opacity-100',
                'text-5xl',
                'text-yellow-500',
              ]"
              style="
                height: 56px;
                width: 56px;
                display: flex;
                align-items: center;
                justify-content: center;
              "
            />
            <span
              :class="[
                'mt-2 text-base tracking-wide',
                selectedIdx === idx ? 'text-white' : 'text-gray-600',
              ]"
              style="
                font-family:
                  'Oswald',
                  Impact,
                  Arial Black,
                  sans-serif;
                letter-spacing: 0.03em;
              "
            >
              {{ role.name }}
            </span>
          </button>
        </div>
      </div>
      <!-- Imagen y selección de personaje -->
      <div class="flex-1 flex flex-col items-center justify-center relative">
        <div
          class="relative w-[340px] h-[340px] md:w-[420px] md:h-[420px] flex items-center justify-center"
        >
          <img
            :src="selected.img"
            :alt="selected.name"
            class="relative z-10 w-[490px] h-[650px] object-contain select-none"
            draggable="false"
          />
        </div>
        <div class="mt-6 text-center">
          <h4 class="text-2xl font-bold text-white mb-1">{{ selected.name }}</h4>
          <p class="text-gray-300 text-sm">{{ selected.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'
import {
  BoltIcon,
  UserGroupIcon,
  SparklesIcon,
  EyeDropperIcon,
  HeartIcon,
  ShieldCheckIcon,
} from '@heroicons/vue/24/solid'

const roles = [
  {
    name: 'ASESINOS',
    icon: BoltIcon,
    character: {
      name: 'EL SOMBRA',
      description: 'Cazador de las tinieblas eternas',
      img: 'https://cmsassets.rgpub.io/sanity/images/dsfx7636/news/befd42ad6d2564159a441d08cfc3bf511532eb74-1628x1628.png?auto=format&fit=fill&q=80&w=1128',
    },
  },
  {
    name: 'LUCHADORES',
    icon: UserGroupIcon,
    character: {
      name: 'EL FORJADOR',
      description: 'Maestro de las armas ancestrales',
      img: 'https://cmsassets.rgpub.io/sanity/images/dsfx7636/news/70c26e49de8a2c79ac3de144772d2debd195edff-1628x1628.png?auto=format&fit=fill&q=80&w=870',
    },
  },
  {
    name: 'MAGOS',
    icon: SparklesIcon,
    character: {
      name: 'LA HECHICERA',
      description: 'Guardiana de los secretos arcanos',
      img: 'https://cmsassets.rgpub.io/sanity/images/dsfx7636/news/ff6c8c57411e5c7e0551b02334fccedc78866143-1628x1628.png?auto=format&fit=fill&q=80&w=870',
    },
  },
  {
    name: 'TIRADORES',
    icon: EyeDropperIcon,
    character: {
      name: 'EL TIRADOR',
      description: 'Precisión letal desde la distancia',
      img: 'https://cmsassets.rgpub.io/sanity/images/dsfx7636/news/f136500bd46f823d37515a72b867425d3a0b3e54-1628x1628.png?auto=format&fit=fill&q=80&w=870',
    },
  },
  {
    name: 'SOPORTES',
    icon: HeartIcon,
    character: {
      name: 'EL GUARDIÁN',
      description: 'Protector y apoyo del equipo',
      img: 'https://cmsassets.rgpub.io/sanity/images/dsfx7636/news/95daf6dd2b28f03d5ba2ea1fabbabc3bc3ff6e6e-1628x1628.png?auto=format&fit=fill&q=80&w=870',
    },
  },
  {
    name: 'TANQUES',
    icon: ShieldCheckIcon,
    character: {
      name: 'EL TITÁN',
      description: 'Resistencia y defensa inquebrantable',
      img: 'https://cmsassets.rgpub.io/sanity/images/dsfx7636/news/dbdded937cd214bb2a1189697a9e4f49f8c04505-1628x1628.png?auto=format&fit=fill&q=80&w=870',
    },
  },
]
const selectedIdx = ref(0)
const selected = computed(() => roles[selectedIdx.value].character)
</script>
