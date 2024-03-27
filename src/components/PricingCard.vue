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
  <div class="prose shadow-md">
    <h2>{{ name }}</h2>
    <p>{{ description }}</p>
    <div>
      <span>${{ price }}</span>
      <span>/month</span>
    </div>
    <ul>
      <li v-for="feature in features" :key="`${name}-${feature}`">
        {{ feature }}
      </li>
    </ul>
    <button>Get started</button>
  </div>
</template>