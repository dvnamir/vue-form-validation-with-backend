<template>
  <div dir="rtl" class="min-h-screen bg-gray-50 flex items-center justify-center p-4">
    <div class="w-full max-w-md">
      <div class="bg-white rounded-lg shadow-md p-8 border border-gray-200">
        <Form @submit="login" class="text-center">
          <h4
            class="text-xl font-bold text-gray-900 mb-6 pb-2 border-b border-gray-300 inline-block"
          >
            ورود
          </h4>

          <div class="space-y-4">
            <div class="relative">
              <Field
                type="text"
                :rules="phoneNumberRule"
                class="w-full px-4 py-2.5 text-right bg-white border border-gray-300 rounded-md focus:border-gray-500 focus:outline-none transition-colors"
                placeholder="شماره تلفن خود را وارد کنید"
                name="phoneNumber"
              />
              <i class="absolute left-3 top-3 text-gray-400 text-lg uil uil-at"></i>
            </div>
            <p class="text-red-500 text-sm mt-1 font-medium">
              <ErrorMessage name="phoneNumber" />
            </p>

            <div class="relative">
              <Field
                type="text"
                :rules="passwordRule"
                class="w-full px-4 py-2.5 text-right bg-white border border-gray-300 rounded-md focus:border-gray-500 focus:outline-none transition-colors"
                placeholder="پسورد را وارد کنید"
                name="password"
              />
              <i class="absolute left-3 top-3 text-gray-400 text-lg uil uil-lock-alt"></i>
            </div>

            <p class="text-red-500 text-sm mt-1 font-medium">
              <ErrorMessage name="password" />
            </p>

            <button
              class="w-full mt-4 bg-gray-900 text-white cursor-pointer py-2.5 rounded-md font-medium hover:bg-gray-800 transition-colors"
            >
              ورود به سایت
            </button>

            <p class="mt-4 text-center">
              <a href="#" class="text-gray-600 hover:text-gray-900 text-sm transition-colors">
                آیا کلمه عبور خود را فراموش کرده اید؟
              </a>
            </p>

            <p class="mt-3 text-center text-sm text-gray-600">
              حساب کاربری ندارید؟
              <a
                href="#"
                @click.prevent="$emit('switch-to-register')"
                class="text-gray-900 hover:underline mr-1 font-medium"
              >
                ثبت نام کنید
              </a>
            </p>
          </div>
        </Form>
      </div>
    </div>
  </div>
</template>

<script setup>
import { Form, Field, ErrorMessage } from 'vee-validate'
import * as yup from 'yup'

defineEmits(['switch-to-register'])

const login = (value) => {
  console.log(value)
}

const phoneNumberRule = yup
  .string()
  .required('شماره تلفن خود را وارد کنید')
  .matches(/^09[0-9]{9}$/, 'شماره موبایل باید با 09 شروع شود و 11 رقم باشد')

const passwordRule = yup
  .string()
  .required('رمز عبور خود را وارد کنید')
  .matches(
    /^(?=.*[A-Z])(?=.*\d)[A-Za-z\d]{8,}$/,
    'رمز عبور باید حداقل ۸ کاراکتر، شامل یک حرف بزرگ و یک عدد باشد',
  )
</script>

<style scoped>
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
