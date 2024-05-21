<template>
  <div v-if="loadingState" class="loader-container load">
    <div class="loader"></div>
  </div>

  <NavBarSection />
  <div class="app">
    <MoviesCard />
    <MovieOutlet />
    <FooterSection />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import NavBarSection from './components/NavBarSection.vue'
import FooterSection from './components/FooterSection.vue'
import MoviesCard from './components/MoviesCard.vue'
import MovieOutlet from './components/MovieOutlet.vue'

const loadingState = ref(true)

onMounted(() => {
  setTimeout(() => {
    loadingState.value = false
  }, 3000)
})
</script>

<style scoped>
.app {
  max-width: 1440px;
  margin: auto;
}
</style>
