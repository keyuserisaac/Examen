<template>
  <div class="d-flex align-items-center justify-content-center min-vh-100">
    <div class="card p-4 shadow-lg" style="max-width: 400px;">
      <h2 class="card-title mb-4 text-center">Por favor inicia sesión</h2>
      <form @submit.prevent="login">
        <div class="mb-3">
          <label for="username" class="form-label">Correo</label>
          <input id="username" v-model="username" type="text" placeholder="Introduce tu correo" required class="form-control" />
        </div>
        <div class="mb-3 position-relative">
          <label for="password" class="form-label">Contraseña</label>
          <input id="password" v-model="password" :type="showPassword ? 'text' : 'password'" placeholder="Introduce tu contraseña" required class="form-control" />
          <button type="button" @click="togglePasswordVisibility" class="btn position-absolute top-50 end-0 translate-middle-y">
            <i :class="showPassword ? 'bi bi-eye-slash' : 'bi bi-eye'"></i>
          </button>
        </div>
        <button type="submit" class="btn btn-primary w-100">Iniciar Sesión</button>
       

      </form>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import { useRouter } from 'vue-router';

const username = ref('');
const password = ref('');
const showPassword = ref(false);
const router = useRouter();

const login = async () => {
  try {
    const { data } = await axios.post('http://localhost:3000/api/login', { Correo: username.value, Contrasena: password.value });
    if (data.token) {
      sessionStorage.setItem('jwt', data.token);
      sessionStorage.setItem('userId', data.id);
      router.push('/crud');
    }
  } catch (error) {
    console.error('Error de inicio de sesión:', error);
  }
};

const togglePasswordVisibility = () => showPassword.value = !showPassword.value;

onMounted(() => {
  if (sessionStorage.getItem('jwt')) router.push('/crud');
});
</script>

<style scoped>
.card {
  border-radius: 10px;
  background: var(--card-bg, #ffffff); /* Fallback color */
  transition: transform 0.3s;
}
.card:hover {
  transform: scale(1.03);
}
.form-control {
  border-radius: 8px;
  border-color: var(--input-border, #d1dace); /* Fallback color */
  color: var(--input-text, #000000); /* Fallback color */
  background: var(--input-bg, #ffffff); /* Fallback color */
  padding: 1rem;
}
.btn-primary {
  background-color: var(--btn-primary-bg, #50acaf); /* Fallback color */
  border-color: var(--btn-primary-border, #dbdbdb); /* Fallback color */
  transition: background-color 0.3s;
}
.btn-primary:hover {
  background-color: var(--btn-primary-hover-bg, #007bff); /* Fallback color */
  border-color: var(--btn-primary-hover-border, #007bff); /* Fallback color */
}
</style>
