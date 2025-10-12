<template>
  <div>
    <AppNavbar />
    <main class="container py-4">
      <RouterView />
    </main>
  </div>
</template>

<script setup>
import AppNavbar from './components/AppNavbar.vue'
</script>

<style scoped>
.navbar-brand {
  font-weight: bold;
}
</style>
