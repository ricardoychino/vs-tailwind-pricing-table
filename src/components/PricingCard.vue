<script setup>
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
  <div class="prose flex flex-col bg-white rounded-md shadow-lg p-4 basis-[300px] h-auto">
    <h2 class="text-center">{{ name }}</h2>
    <p class="text-gray-400 text-center font-light ">{{ description }}</p>
    <div class="text-center my-2">
      <span class="font-bold text-4xl">${{ price }}</span>
      <span class="text-gray-400 ml-2 text-md">/month</span>
    </div>
    <ul class="mb-8">
      <li v-for="feature in features"
        :key="`${name}-${feature}`"
        class="text-sm mb-3"
        >
        {{ feature }}
      </li>
    </ul>
    <button class="w-full rounded-md p-2 mt-auto bg-blue-700 text-white hover:bg-blue-800 transition">
      Get started
    </button>
  </div>
</template>