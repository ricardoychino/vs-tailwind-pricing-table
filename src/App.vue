<script setup>
import { reactive } from "vue";
import { pricing } from "@/pricing.json"
import PricingCard from "@/components/PricingCard.vue"

const items = reactive(pricing)
</script>

<template>
  <main class="flex justify-center items-center gap-5 py-10 w-[100vw] h-[100vh]">
    <PricingCard v-for="item in items"
      :name="item.name"
      :price="item.price"
      :description="item.description"
      :features="item.features"
      :key="item.name.toLowerCase()"
    />
  </main>
</template>
