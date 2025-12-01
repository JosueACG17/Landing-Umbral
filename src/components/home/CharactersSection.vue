<template>
  <section
    id="campeones"
    class="min-h-screen py-20 bg-gradient-to-b from-black via-gray-900 to-black flex items-center overflow-hidden relative"
  >
    <div
      class="absolute inset-0 transition-all duration-1000"
      :class="
        showVillains
          ? 'bg-[radial-gradient(ellipse_at_center,rgba(220,38,38,0.15)_0%,transparent_70%)]'
          : 'bg-[radial-gradient(ellipse_at_center,rgba(234,179,8,0.15)_0%,transparent_70%)]'
      "
    ></div>

    <div
      class="container mx-auto max-w-7xl grid grid-cols-1 xl:grid-cols-2 gap-12 px-6 relative z-10"
    >
      <!-- Columna Texto -->
      <div
        class="flex flex-col justify-center items-center xl:items-start text-center xl:text-left order-1"
      >
        <!-- Botones -->
        <div
          class="mb-6 flex gap-2 bg-gray-900/80 backdrop-blur-sm rounded-full p-1.5 border-2 border-gray-700/50"
        >
          <button
            @click="showVillains = false"
            :class="
              !showVillains
                ? 'bg-gradient-to-r from-yellow-400 to-yellow-600 text-black shadow-2xl shadow-yellow-500/60 scale-105'
                : 'text-gray-400 hover:text-white hover:bg-gray-800/50'
            "
            class="px-8 py-3 rounded-full font-bold transition-all duration-500 flex items-center gap-2"
          >
            <svg v-if="!showVillains" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20">
              <path
                d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"
              />
            </svg>
            CAZADORES
          </button>
          <button
            @click="showVillains = true"
            :class="
              showVillains
                ? 'bg-gradient-to-r from-red-600 to-red-800 text-white shadow-2xl shadow-red-600/60 scale-105'
                : 'text-gray-400 hover:text-white hover:bg-gray-800/50'
            "
            class="px-8 py-3 rounded-full font-bold transition-all duration-500 flex items-center gap-2"
          >
            <svg v-if="showVillains" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20">
              <path
                fill-rule="evenodd"
                d="M12.395 2.553a1 1 0 00-1.45-.385c-.345.23-.614.558-.822.88-.214.33-.403.713-.57 1.116-.334.804-.614 1.768-.84 2.734a31.365 31.365 0 00-.613 3.58 2.64 2.64 0 01-.945-1.067c-.328-.68-.398-1.534-.398-2.654A1 1 0 005.05 6.05 6.981 6.981 0 003 11a7 7 0 1011.95-4.95c-.592-.591-.98-.985-1.348-1.467-.363-.476-.724-1.063-1.207-2.03zM12.12 15.12A3 3 0 017 13s.879.5 2.5.5c0-1 .5-4 1.25-4.5.5 1 .786 1.293 1.371 1.879A2.99 2.99 0 0113 13a2.99 2.99 0 01-.879 2.121z"
                clip-rule="evenodd"
              />
            </svg>
            ENEMIGOS
          </button>
        </div>

        <h3 class="text-lg text-gray-300 mb-2 tracking-widest uppercase">DESCUBRE A LOS</h3>

        <transition name="fade" mode="out-in">
          <h2
            :key="showVillains ? 'villains' : 'heroes'"
            class="text-5xl lg:text-7xl font-extrabold mb-6 drop-shadow-2xl"
            :class="showVillains ? 'text-red-500' : 'text-yellow-400'"
            style="font-family: 'Oswald', Impact, 'Arial Black', sans-serif"
          >
            {{ showVillains ? 'ENEMIGOS' : 'CAZADORES' }}
          </h2>
        </transition>

        <transition name="fade" mode="out-in">
          <p
            :key="showVillains ? 'villains' : 'heroes'"
            class="text-lg text-gray-300 mb-6 max-w-md leading-relaxed bg-black/20 p-4 rounded-lg border border-gray-700/30"
          >
            {{
              showVillains
                ? 'Las sombras también tienen sus enemigos. ¿Te atreves a desatar la oscuridad?'
                : 'Cada cazador tiene un rol fundamental. Elige tu favorito y llega a la victoria.'
            }}
          </p>
        </transition>

        <!-- Roles -->
        <transition name="fade" mode="out-in">
          <div
            :key="showVillains ? 'villains' : 'heroes'"
            class="grid grid-cols-4 gap-4 sm:gap-0 mt-8 w-full max-w-lg mx-auto xl:mx-0"
          >
            <button
              v-for="(role, idx) in currentRoles"
              :key="role.name"
              @click="selectedIdx = idx"
              class="flex flex-col items-center group transition-all duration-300 hover:-translate-y-2 cursor-pointer relative z-20"
            >
              <div
                :class="[
                  'p-5 rounded-2xl backdrop-blur-md transition-all duration-300 border-2 pointer-events-none',
                  selectedIdx === idx
                    ? showVillains
                      ? 'bg-red-900/30 border-red-500/50 shadow-2xl shadow-red-500/50'
                      : 'bg-yellow-900/30 border-yellow-500/50 shadow-2xl shadow-yellow-500/50'
                    : 'bg-gray-800/30 border-gray-700/30 group-hover:bg-gray-700/50',
                ]"
              >
                <component
                  :is="role.icon"
                  :class="[
                    'w-8 h-8 sm:w-12 sm:h-12 transition-all',
                    selectedIdx === idx ? 'scale-110' : 'opacity-70 group-hover:opacity-100',
                    showVillains ? 'text-red-500' : 'text-yellow-400',
                  ]"
                />
              </div>
              <span
                :class="[
                  'mt-2 sm:mt-3 text-xs sm:text-sm tracking-widest transition-all pointer-events-none',
                  selectedIdx === idx
                    ? showVillains
                      ? 'text-red-400'
                      : 'text-yellow-400'
                    : 'text-white',
                ]"
                style="font-family: 'Oswald', Impact, 'Arial Black', sans-serif"
                >{{ role.name }}</span
              >
            </button>
          </div>
        </transition>
      </div>

      <!-- Columna Imagen -->
      <div class="flex flex-col items-center justify-center relative order-2">
        <div
          class="relative w-[400px] h-[400px] xl:w-[500px] xl:h-[500px] flex items-center justify-center"
        >
          <div
            class="absolute w-full h-full rounded-full animate-pulse-slow"
            :class="
              showVillains
                ? 'bg-gradient-to-r from-red-600/40 to-red-800/40'
                : 'bg-gradient-to-r from-yellow-500/40 to-yellow-700/40'
            "
            style="filter: blur(40px)"
          ></div>
          <div
            class="absolute w-[105%] h-[105%] rounded-full border-2 animate-spin-slow"
            :class="showVillains ? 'border-red-600/30' : 'border-yellow-500/30'"
          ></div>
          <div
            class="absolute w-[95%] h-[95%] rounded-full border-2 animate-reverse-spin"
            :class="showVillains ? 'border-red-500/50' : 'border-yellow-500/50'"
          ></div>

          <transition name="character-slide" mode="out-in">
            <div
              :key="`${showVillains}-${selectedIdx}`"
              class="relative z-10 transition-all duration-700 hover:scale-105"
            >
              <img
                :src="selected.img"
                :alt="selected.name"
                :class="selected.class || 'w-[380px] h-[380px] xl:w-[480px] xl:h-[500px]'"
                class="object-contain drop-shadow-2xl"
                :style="
                  showVillains
                    ? 'filter: drop-shadow(0 0 40px rgba(220, 38, 38, 0.8))'
                    : 'filter: drop-shadow(0 0 40px rgba(234, 179, 8, 0.8))'
                "
              />
            </div>
          </transition>
        </div>

        <transition name="fade" mode="out-in">
          <div
            :key="`${showVillains}-${selectedIdx}`"
            class="mt-8 text-center backdrop-blur-lg p-6 rounded-2xl border-2 w-full max-w-md shadow-2xl"
            :class="
              showVillains
                ? 'bg-red-950/40 border-red-500/30'
                : 'bg-yellow-950/40 border-yellow-500/30'
            "
          >
            <h4
              class="text-3xl font-bold mb-2"
              :class="showVillains ? 'text-red-500' : 'text-yellow-400'"
              style="font-family: 'Oswald', Impact, 'Arial Black', sans-serif"
            >
              {{ selected.name }}
            </h4>
            <div
              class="w-24 h-1 mx-auto mb-3 rounded-full"
              :class="
                showVillains
                  ? 'bg-gradient-to-r from-transparent via-red-500 to-transparent'
                  : 'bg-gradient-to-r from-transparent via-yellow-400 to-transparent'
              "
            ></div>
            <p class="text-gray-300 text-base">{{ selected.description }}</p>
          </div>
        </transition>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, computed, watch } from 'vue'
import {
  BoltIcon,
  UserGroupIcon,
  SparklesIcon,
  EyeDropperIcon,
  FireIcon,
  ShieldExclamationIcon,
} from '@heroicons/vue/24/solid'
import vikingoImage from '@/assets/Berserkerr.png'
import gladiadorImage from '@/assets/Tanquee.png'
import magoImage from '@/assets/Magoo.png'
import tiradorImage from '@/assets/Arquero.png'
import subditoImage from '@/assets/Subdito.png'
import jefeImage from '@/assets/Jefe.png'

const showVillains = ref(false)
const selectedIdx = ref(0)

const heroes = [
  {
    name: 'Berserker',
    icon: BoltIcon,
    character: {
      name: 'GRAK',
      description: 'Cazador de las tinieblas eternas',
      img: vikingoImage,
      class: '',
    },
  },
  {
    name: 'Tanque',
    icon: UserGroupIcon,
    character: {
      name: 'HAROLD',
      description: 'Maestro de las armas ancestrales',
      img: gladiadorImage,
      class: '',
    },
  },
  {
    name: 'Mago',
    icon: SparklesIcon,
    character: {
      name: 'ELANDOR',
      description: 'Guardian de los secretos arcanos',
      img: magoImage,
      class: '',
    },
  },
  {
    name: 'Tirador',
    icon: EyeDropperIcon,
    character: {
      name: 'KAITO',
      description: 'Precisión letal desde la distancia',
      img: tiradorImage,
      class: 'w-[340px] h-[300px] xl:w-[400px] xl:h-[350px]',
    },
  },
]

const villains = [
  {
    name: 'Subdito',
    icon: FireIcon,
    character: {
      name: 'Subdito',
      description: 'Señor del caos y la destrucción',
      img: subditoImage,
      class: '',
    },
  },
  {
    name: 'Guardian',
    icon: ShieldExclamationIcon,
    character: {
      name: 'Guardian',
      description: 'Asesino implacable de las sombras',
      img: jefeImage,
      class: 'w-[300px] h-[300px] xl:w-[400px] xl:h-[400px]',
    },
  },
]

const currentRoles = computed(() => (showVillains.value ? villains : heroes))
const selected = computed(() => currentRoles.value[selectedIdx.value].character)

watch(showVillains, () => {
  selectedIdx.value = 0
})
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: all 0.4s ease;
}
.fade-enter-from {
  opacity: 0;
  transform: translateY(15px);
}
.fade-leave-to {
  opacity: 0;
  transform: translateY(-15px);
}

.character-slide-enter-active,
.character-slide-leave-active {
  transition: all 0.5s ease-in-out;
}
.character-slide-enter-from {
  opacity: 0;
  transform: scale(0.9) translateY(20px);
}
.character-slide-leave-to {
  opacity: 0;
  transform: scale(0.9) translateY(-20px);
}

@keyframes pulse-slow {
  0%,
  100% {
    opacity: 0.6;
    transform: scale(2);
  }
  50% {
    opacity: 1;
    transform: scale(2.2);
  }
}
.animate-pulse-slow {
  animation: pulse-slow 4s ease-in-out infinite;
}

@keyframes spin-slow {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
.animate-spin-slow {
  animation: spin-slow 30s linear infinite;
}

@keyframes reverse-spin {
  from {
    transform: rotate(360deg);
  }
  to {
    transform: rotate(0deg);
  }
}
.animate-reverse-spin {
  animation: reverse-spin 25s linear infinite;
}
</style>
