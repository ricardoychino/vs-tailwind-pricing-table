<script setup>
import CheckIcon from '@/components/CheckIcon.vue'

defineProps({
  name: {
    type: String,
    required: true
  },
  price: Number,
  description: String,
  features: {
    default: []
  }
})
</script>

<template>
  <div class="prose flex flex-col rounded-md box-border text-center shadow-lg p-4 h-auto border bg-white border-slate-50 dark:bg-slate-700 dark:text-slate-100 dark:border-slate-600">
    <h2 class="dark:text-white">{{ name }}</h2>
    <p class="font-light text-gray-400 dark:text-gray-500">{{ description }}</p>
    <div class="my-2">
      <span class="font-bold text-4xl">${{ price }}</span>
      <span class="ml-2 text-md text-gray-400 dark:text-gray-500">/month</span>
    </div>
    <ul class="mb-8 p-0 text-left">
      <li v-for="feature in features"
        :key="`${name}-${feature}`"
        class="flex items-center text-sm mb-3"
        >
        <CheckIcon class="mr-1" />
        {{ feature }}
      </li>
    </ul>
    <button class="w-full rounded-md p-2 mt-auto bg-blue-700 text-white hover:bg-blue-800 transition">
      Get started
    </button>
  </div>
</template>