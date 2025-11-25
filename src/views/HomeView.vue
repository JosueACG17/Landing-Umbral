<template>
  <div class="min-h-screen bg-black text-white overflow-x-hidden">
    <Navigation />
    <HeroSection />
    <WelcomeBanner />
    <CharactersSection />
    <FeaturesComponent />
    <NewsComponent />
    <FooterSection />
  </div>
</template>

<script setup lang="ts">
import Navigation from '@/components/home/NavigationComponent.vue'
import HeroSection from '@/components/home/HeroSection.vue'
import WelcomeBanner from '@/components/home/WelcomeBanner.vue'
import CharactersSection from '@/components/home/CharactersSection.vue'
import FeaturesComponent from '@/components/home/FeaturesComponent.vue'
import NewsComponent from '@/components/home/AppComponent.vue'
import FooterSection from '@/components/home/FooterSection.vue'
</script>

<style scoped>
/* Custom scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #1a1a1a;
}

::-webkit-scrollbar-thumb {
  background: #4c1d95;
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: #5b21b6;
}

/* Smooth scrolling */
html {
  scroll-behavior: smooth;
}

/* Custom animations */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fadeInUp {
  animation: fadeInUp 0.6s ease-out;
}
</style>
