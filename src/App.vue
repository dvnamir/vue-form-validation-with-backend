<template>
  <div>
    <register-form v-if="showRegister" @switch-to-login="showRegister = false"></register-form>
    <login-form v-else @switch-to-register="showRegister = true"></login-form>
  </div>
</template>

<script setup>
import { ref } from 'vue'

import LoginForm from './components/LoginForm.vue'
import RegisterForm from './components/RegisterForm.vue'

const showRegister = ref(true)
</script>

<style scoped></style>
