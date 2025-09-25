<template>
  <div
    class="group relative bg-gray-900/50 backdrop-blur-sm border border-gray-700 rounded-lg overflow-hidden hover:border-purple-500 transition-all duration-300"
  >
    <div
      class="aspect-square bg-gradient-to-b from-gray-800 to-gray-900 flex items-center justify-center"
    >
      <img
        :src="img"
        :alt="name"
        class="w-full h-full object-cover opacity-80 group-hover:opacity-100 transition-opacity"
      />
    </div>
    <div class="p-6">
      <h3 class="text-xl font-bold text-white mb-2">{{ name }}</h3>
      <p class="text-gray-400 text-sm">{{ description }}</p>
    </div>
  </div>
</template>
<script setup lang="ts">
defineProps<{ name: string; description: string; img: string }>()
</script>
