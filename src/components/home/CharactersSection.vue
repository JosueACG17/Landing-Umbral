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
          <!-- Círculo decorativo -->
          <div
            class="absolute w-full h-full rounded-full bg-gradient-to-r from-yellow-500/30 to-yellow-700/30 animate-pulse"
          ></div>
          <div class="absolute w-[95%] h-[95%] rounded-full border-2 border-yellow-500/50"></div>
          <img
            :src="selected.img"
            :alt="selected.name"
            class="relative z-10 w-[490px] h-[450px] object-contain select-none"
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
import { BoltIcon, UserGroupIcon, SparklesIcon, EyeDropperIcon } from '@heroicons/vue/24/solid'

import vikingoImage from '@/assets/vikingo_game.png'
import gladiadorImage from '@/assets/gladiador_game.png'
import magoImage from '@/assets/mago_game.png'
import tiradorImage from '@/assets/tirador_game.png'

const roles = [
  {
    name: 'ASESINOS',
    icon: BoltIcon,
    character: {
      name: 'EL SOMBRA',
      description: 'Cazador de las tinieblas eternas',
      img: vikingoImage,
    },
  },
  {
    name: 'LUCHADORES',
    icon: UserGroupIcon,
    character: {
      name: 'EL FORJADOR',
      description: 'Maestro de las armas ancestrales',
      img: gladiadorImage,
    },
  },
  {
    name: 'MAGOS',
    icon: SparklesIcon,
    character: {
      name: 'EL HECHICERO',
      description: 'Guardian de los secretos arcanos',
      img: magoImage,
    },
  },
  {
    name: 'TIRADORES',
    icon: EyeDropperIcon,
    character: {
      name: 'EL TIRADOR',
      description: 'Precisión letal desde la distancia',
      img: tiradorImage,
    },
  },
]
const selectedIdx = ref(0)
const selected = computed(() => roles[selectedIdx.value].character)
</script>
