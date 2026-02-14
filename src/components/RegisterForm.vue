<template>
  <div dir="rtl" class="min-h-screen bg-gray-50 flex items-center justify-center p-4">
    <div class="w-full max-w-md">
      <div class="bg-white rounded-lg shadow-md p-8 border border-gray-200">
        <Form @submit="register" class="text-center" :validation-schema="registerFormSchema">
          <h4
            class="text-xl font-bold text-gray-900 mb-6 pb-2 border-b border-gray-300 inline-block"
          >
            ثبت نام
          </h4>

          <div class="space-y-4">
            <div class="relative">
              <Field
                type="text"
                class="w-full px-4 py-2.5 text-right bg-white border border-gray-300 rounded-md focus:border-gray-500 focus:outline-none transition-colors"
                placeholder="نام و نام خانوادگی"
                name="name"
                autocomplete="off"
                :validateOnInput="true"
              />
              <i class="absolute left-3 top-3 text-gray-400 text-lg uil uil-user"></i>
            </div>
            <p class="text-red-500 text-sm mt-1 font-medium">
              <ErrorMessage name="name" />
            </p>

            <div class="relative">
              <Field
                type="email"
                class="w-full px-4 py-2.5 text-right bg-white border border-gray-300 rounded-md focus:border-gray-500 focus:outline-none transition-colors"
                placeholder="ایمیل خود را وارد کنید"
                name="email"
                autocomplete="off"
                :validateOnInput="true"
              />
              <i class="absolute left-3 top-3 text-gray-400 text-lg uil uil-at"></i>
            </div>

            <p class="text-red-500 text-sm mt-1 font-medium">
              <ErrorMessage name="email" />
            </p>

            <div class="relative">
              <Field
                type="text"
                class="w-full px-4 py-2.5 text-right bg-white border border-gray-300 rounded-md focus:border-gray-500 focus:outline-none transition-colors"
                placeholder="شماره تلفن"
                name="phoneNumber"
                autocomplete="off"
                :validateOnInput="true"
              />
              <i class="absolute left-3 top-3 text-gray-400 text-lg uil uil-at"></i>
            </div>

            <p class="text-red-500 text-sm mt-1 font-medium">
              <ErrorMessage name="phoneNumber" />
            </p>

            <div class="relative">
              <Field
                type="password"
                class="w-full px-4 py-2.5 text-right bg-white border border-gray-300 rounded-md focus:border-gray-500 focus:outline-none transition-colors"
                placeholder="کلمه عبور"
                name="password"
                autocomplete="off"
                :validateOnInput="true"
              />
              <i class="absolute left-3 top-3 text-gray-400 text-lg uil uil-lock-alt"></i>
            </div>

            <p class="text-red-500 text-sm mt-1 font-medium">
              <ErrorMessage name="password" />
            </p>

            <div class="relative">
              <Field
                type="password"
                class="w-full px-4 py-2.5 text-right bg-white border border-gray-300 rounded-md focus:border-gray-500 focus:outline-none transition-colors"
                placeholder="تکرار کلمه عبور"
                name="confirmPassword"
                autocomplete="off"
                :validateOnInput="true"
              />
              <i class="absolute left-3 top-3 text-gray-400 text-lg uil uil-lock-alt"></i>
            </div>

            <p class="text-red-500 text-sm mt-1 font-medium">
              <ErrorMessage name="confirmPassword" />
            </p>

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
        </Form>
      </div>
    </div>
  </div>
</template>

<script setup>
import { Form, Field, ErrorMessage } from 'vee-validate'
import { object, string, ref } from 'yup'

defineEmits(['switch-to-login'])

const registerFormSchema = object({
  name: string()
    .min(3, 'حداقل ۳ حرف')
    .max(30, 'حداکثر دارای ۳۰ حرف')
    .matches(/^[آ-یa-zA-Z\s]+$/, 'فقط حروف و فاصله مجاز است'),
  email: string().required('ایمیل خود را وارد کنید').email('ایمیل معتبر نیست'),
  phoneNumber: string()
    .required('شماره تلفن خود را وارد کنید')
    .matches(/^09[0-9]{9}$/, 'شماره موبایل باید با 09 شروع شود و 11 رقم باشد'),
  password: string()
    .required('رمز عبور خود را وارد کنید')
    .matches(
      /^(?=.*[A-Z])(?=.*\d)[A-Za-z\d]{8,}$/,
      'رمز عبور باید حداقل ۸ کاراکتر، شامل یک حرف بزرگ و یک عدد باشد',
    ),
  confirmPassword: string()
    .required('تکرار رمز عبور را وارد کنید')
    .oneOf([ref('password')], 'رمز عبور و تکرار آن یکسان نیست'),
})

const register = (value) => {
  console.log(value)
}
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
