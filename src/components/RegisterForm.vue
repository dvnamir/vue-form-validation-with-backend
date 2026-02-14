<template>
  <div dir="rtl" class="min-h-screen bg-gray-50 flex items-center justify-center p-4">
    <div class="w-full max-w-md">
      <div class="bg-white rounded-lg shadow-md p-8 border border-gray-200">
        <div @submit="register.prevent" class="text-center">
          <h4
            class="text-xl font-bold text-gray-900 mb-6 pb-2 border-b border-gray-300 inline-block"
          >
            ثبت نام
          </h4>

          <div class="space-y-4">
            <div class="relative">
              <input
                type="text"
                class="w-full px-4 py-2.5 text-right bg-white border border-gray-300 rounded-md focus:border-gray-500 focus:outline-none transition-colors"
                placeholder="نام و نام خانوادگی"
                v-model="name"
                autocomplete="off"
              />
              <i class="absolute left-3 top-3 text-gray-400 text-lg uil uil-user"></i>
            </div>

            <div class="relative">
              <input
                type="email"
                class="w-full px-4 py-2.5 text-right bg-white border border-gray-300 rounded-md focus:border-gray-500 focus:outline-none transition-colors"
                placeholder="ایمیل خود را وارد کنید"
                v-model="email"
                autocomplete="off"
              />
              <i class="absolute left-3 top-3 text-gray-400 text-lg uil uil-at"></i>
            </div>

            <div class="relative">
              <input
                type="text"
                class="w-full px-4 py-2.5 text-right bg-white border border-gray-300 rounded-md focus:border-gray-500 focus:outline-none transition-colors"
                placeholder="شماره تلفن"
                v-model="phoneNumber"
                autocomplete="off"
              />
              <i class="absolute left-3 top-3 text-gray-400 text-lg uil uil-at"></i>
            </div>

            <div class="relative">
              <input
                type="password"
                class="w-full px-4 py-2.5 text-right bg-white border border-gray-300 rounded-md focus:border-gray-500 focus:outline-none transition-colors"
                placeholder="کلمه عبور"
                v-model="password"
                autocomplete="off"
              />
              <i class="absolute left-3 top-3 text-gray-400 text-lg uil uil-lock-alt"></i>
            </div>

            <div class="relative">
              <input
                type="password"
                class="w-full px-4 py-2.5 text-right bg-white border border-gray-300 rounded-md focus:border-gray-500 focus:outline-none transition-colors"
                placeholder="تکرار کلمه عبور"
                v-model="confirmPassword"
                autocomplete="off"
              />
              <i class="absolute left-3 top-3 text-gray-400 text-lg uil uil-lock-alt"></i>
            </div>

            <button
              class="w-full mt-4 bg-gray-900 text-white cursor-pointer py-2.5 rounded-md font-medium hover:bg-gray-800 transition-colors"
            >
              ثبت نام
            </button>

            <p class="mt-4 text-center text-sm text-gray-600">
              قبلاً ثبت نام کرده اید؟
              <a
                href="#"
                @click.prevent="$emit('switch-to-login')"
                class="text-gray-900 hover:underline mr-1 font-medium"
              >
                وارد شوید
              </a>
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

defineEmits(['switch-to-login'])

const name = ref('')
const email = ref('')
const phoneNumber = ref('')
const password = ref('')
const confirmPassword = ref('')

const register = () => {
  console.log(name)
  console.log(email)
  console.log(phoneNumber)
  console.log(password)
  console.log(confirmPassword)
}
</script>

<style scoped>
/* ریسپانسیو برای موبایل */
@media (max-width: 640px) {
  .text-2xl {
    font-size: 1.5rem;
  }

  .py-3 {
    padding-top: 0.75rem;
    padding-bottom: 0.75rem;
  }
}
</style>
