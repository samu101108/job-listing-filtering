<script setup>
import TheHeader from './components/TheHeader.vue';
import TheCardsList from './components/TheCardsList.vue'
import TheFilter from './components/TheFilter.vue'
</script>

<template>
  <header>
    <TheHeader />
    <TheFilter />
  </header>

  <main>
    <TheCardsList />
  </main>
</template>

<style scoped>
</style>
