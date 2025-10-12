<template>
  <div>
    <h2 class="h4 mb-3">Dashboard</h2>
    <div class="alert alert-success">You are logged in.</div>
    <div v-if="me" class="card">
      <div class="card-body">
        <h5 class="card-title mb-2">Welcome, {{ me.firstName }} {{ me.lastName }}</h5>
        <p class="mb-0 text-muted">Username: {{ me.username }} • Email: {{ me.email }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { http } from '../api/http'
const me = ref(null)
onMounted(async () => {
  try {
    const { data } = await http.get('/auth/me')
    me.value = data
  } catch (e) {
    me.value = null
  }
})
</script>