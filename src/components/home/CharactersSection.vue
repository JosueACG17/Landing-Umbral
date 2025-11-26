<template>
  <section
    id="campeones"
    class="py-20 bg-gradient-to-b from-black via-gray-900 to-black flex justify-center items-center overflow-hidden"
  >
    <div
      class="w-full max-w-7xl flex flex-col md:flex-row items-center md:items-stretch gap-8 px-4 sm:px-6 lg:px-8 relative z-10"
    >
      <div
        class="flex-1 flex flex-col justify-center items-center md:items-start text-center md:text-left fade-in"
        style="animation-delay: 0.1s"
      >
        <div class="mb-6 flex items-center gap-4 bg-gray-800/50 rounded-full p-2 border border-gray-700">
          <button
            @click="showVillains = false"
            :class="[
              'px-6 py-2 rounded-full font-bold transition-all duration-300',
              !showVillains
                ? 'bg-yellow-500 text-black shadow-lg shadow-yellow-500/50'
                : 'text-gray-400 hover:text-white'
            ]"
          >
            CAZADORES
          </button>
          <button
            @click="showVillains = true"
            :class="[
              'px-6 py-2 rounded-full font-bold transition-all duration-300',
              showVillains
                ? 'bg-red-600 text-white shadow-lg shadow-red-600/50'
                : 'text-gray-400 hover:text-white'
            ]"
          >
            ENEMIGOS
          </button>
        </div>

        <h3 class="text-lg text-gray-200 mb-2 tracking-widest uppercase">DESCUBRE A LOS</h3>

        <transition name="fade" mode="out-in">
          <h2
            :key="showVillains ? 'villains-title' : 'heroes-title'"
            class="text-4xl sm:text-6xl font-extrabold mb-4 drop-shadow"
            :class="showVillains ? 'text-red-500' : 'text-yellow-400'"
            style="
              font-family: 'Oswald', Impact, 'Arial Black', sans-serif;
              letter-spacing: 0.03em;
            "
          >
            <span :class="showVillains ? 'text-red-600 animate-pulse' : 'text-yellow-500 animate-pulse'">
              {{ showVillains ? 'ENEMIGOS' : 'CAZADORES' }}
            </span>
          </h2>
        </transition>
        <transition name="fade" mode="out-in">
          <p
            :key="showVillains ? 'villains-desc' : 'heroes-desc'"
            class="text-base  text-gray-300 mb-6 max-w-md "
          >
            {{ showVillains
              ? 'Las sombras también tienen sus enemigos. Cada uno tiene una sed de caos. ¿Te atreves a desatar la oscuridad?'
              : 'Cada personaje tiene una historia y un rol fundamental en la batalla. Elige tu favorito, domina su estilo y llega a la victoria. ¡El destino del Reino está en tus manos!'
            }}
          </p>
        </transition>

        <transition name="fade" mode="out-in">
          <div
            :key="showVillains ? 'villains-roles' : 'heroes-roles'"
            class="flex flex-row flex-wrap gap-8 justify-center md:justify-start mt-8"
          >
            <button
              v-for="(role, idx) in currentRoles"
              :key="role.name"
              @click="selectedIdx = idx"
              class="flex flex-col items-center group focus:outline-none relative"
            >
              <div
                v-if="selectedIdx === idx"
                class="absolute inset-0 rounded-full blur-xl animate-pulse"
                :style="showVillains
                  ? 'background: rgba(220, 38, 38, 0.4); transform: scale(1.5)'
                  : 'background: rgba(234, 179, 8, 0.4); transform: scale(1.5)'"
              ></div>

              <component
                :is="role.icon"
                :class="[
                  'mb-2 transition-all cursor-pointer relative z-10',
                  selectedIdx === idx
                    ? 'scale-125 drop-shadow-lg'
                    : 'opacity-60 group-hover:opacity-100 group-hover:scale-110',
                  'text-5xl',
                  showVillains ? 'text-red-600' : 'text-yellow-500',
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
                  'mt-2 text-base tracking-wide transition-all',
                  selectedIdx === idx ? 'text-white' : 'text-gray-600',
                ]"
                style="
                  font-family: 'Oswald', Impact, 'Arial Black', sans-serif;
                  letter-spacing: 0.03em;
                "
              >
                {{ role.name }}
              </span>
            </button>
          </div>
        </transition>
      </div>

      <div class="flex-1 flex flex-col items-center justify-center relative">
        <div
          class="relative w-[340px] h-[340px] md:w-[420px] md:h-[420px] flex items-center justify-center"
        >
          <div
            class="absolute w-full h-full rounded-full animate-pulse"
            :class="showVillains
              ? 'bg-gradient-to-r from-red-600/30 to-red-800/30'
              : 'bg-gradient-to-r from-yellow-500/30 to-yellow-700/30'"
          ></div>
          <div
            class="absolute w-[95%] h-[95%] rounded-full border-2"
            :class="showVillains ? 'border-red-600/50' : 'border-yellow-500/50'"
          ></div>

          <transition name="character-fade" mode="out-in">
            <img
              :key="`${showVillains}-${selectedIdx}`"
              :src="selected.img"
              :alt="selected.name"
              :class="[
                'relative z-10 object-contain select-none',
                selected.class
                  ? selected.class
                  : 'w-[380px] h-[380px] sm:w-[320px] sm:h-[320px] md:w-[450px] md:h-[470px]',
              ]"
              draggable="false"
            />
          </transition>
        </div>

        <transition name="fade" mode="out-in">
          <div :key="`${showVillains}-${selectedIdx}`" class="mt-6 text-center">
            <h4
              class="text-2xl font-bold animate-pulse mb-1"
              :class="showVillains ? 'text-red-600' : 'text-yellow-500'"
            >
              {{ selected.name }}
            </h4>
            <p class="text-gray-300 text-sm">{{ selected.description }}</p>
          </div>
        </transition>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, computed, onMounted, watch } from 'vue'
import { BoltIcon, UserGroupIcon, SparklesIcon, EyeDropperIcon, FireIcon, ShieldExclamationIcon} from '@heroicons/vue/24/solid'

import vikingoImage from '@/assets/Berserkerr.png'
import gladiadorImage from '@/assets/Tanquee.png'
import magoImage from '@/assets/Magoo.png'
import tiradorImage from '@/assets/Arquero.png'
import subditoImage from '@/assets/Subdito.png'
import jefeImage from '@/assets/Jefe.png'

const showVillains = ref(false)

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
      class: 'w-[340px] h-[300px] sm:w-[300px] sm:h-[270px] md:w-[400px] md:h-[350px]',
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
    name: 'Guardian del Umbral',
    icon: ShieldExclamationIcon,
    character: {
      name: 'Guardian',
      description: 'Asesino implacable de las sombras',
      img: jefeImage,
      class: 'w-[300px] h-[300px] sm:w-[250px] sm:h-[250px] md:w-[400px] md:h-[400px]',
    },
  },
]

const selectedIdx = ref(0)

const currentRoles = computed(() => showVillains.value ? villains : heroes)
const selected = computed(() => currentRoles.value[selectedIdx.value].character)

watch(showVillains, () => {
  selectedIdx.value = 0
})

onMounted(() => {
  [...heroes, ...villains].forEach(r => {
    const img = new Image()
    img.src = r.character.img
  })
})
</script>

<style scoped>
/* Transición suave del personaje */
.character-fade-enter-active,
.character-fade-leave-active {
  transition: all 0.4s ease;
}

.character-fade-enter-from {
  opacity: 0;
  transform: scale(0.9);
}

.character-fade-leave-to {
  opacity: 0;
  transform: scale(0.9);
}

/* Transición del texto */
.fade-enter-active,
.fade-leave-active {
  transition: all 0.3s ease;
}

.fade-enter-from {
  opacity: 0;
  transform: translateY(10px);
}

.fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
