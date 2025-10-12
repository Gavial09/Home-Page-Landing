<template>
  <div class="row justify-content-center">
    <div class="col-md-5">
      <div class="card shadow-sm">
        <div class="card-body">
          <h1 class="h5 mb-3">Sign in</h1>
          <form @submit.prevent="onSubmit">
            <div class="mb-3">
              <label class="form-label">Username</label>
              <input v-model.trim="username" type="text" class="form-control" placeholder="username" required />
            </div>
            <div class="mb-3">
              <label class="form-label">Password</label>
              <input v-model.trim="password" type="password" class="form-control" placeholder="password" required />
            </div>
            <button class="btn btn-primary w-100" :disabled="loading">
              <span v-if="loading" class="spinner-border spinner-border-sm me-2"></span>Login
            </button>
            <p v-if="error" class="text-danger mt-3">{{ error }}</p>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter, useRoute } from 'vue-router'
import { useAuthStore } from '../stores/auth'
import { http } from '../api/http'
const username = ref(''); const password = ref(''); const loading = ref(false); const error = ref('');
const auth = useAuthStore(); const router = useRouter(); const route = useRoute();

async function onSubmit(){
  error.value = ''; loading.value = true
  try {
    console.log('Attempting login with:', { username: username.value, password: password.value })
    const { data } = await http.post('/auth/login', { username: username.value, password: password.value })
    console.log('Login response:', data)
    // DummyJSON returns accessToken & many user fields in one object
    const user = {
      id: data.id,
      username: data.username,
      email: data.email,
      name: [data.firstName, data.lastName].filter(Boolean).join(' ')
    }
    auth.setAuth({ token: data.accessToken, user })
    router.push(route.query.redirect || '/dashboard')
  } catch (e) { 
    console.error('Login error:', e)
    console.error('Error response:', e.response?.data)
    console.error('Error status:', e.response?.status)
    error.value = `Login failed: ${e.response?.data?.message || e.response?.statusText || e.message || 'Invalid credentials or server error.'}`
  }
  finally { loading.value = false }
}
</script>