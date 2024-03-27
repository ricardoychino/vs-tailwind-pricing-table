<script setup>
import { reactive } from "vue";
import { pricing } from "@/pricing.json"
import PricingCard from "@/components/PricingCard.vue"
import ToggleButton from "@/components/ToggleButton.vue"


const items = reactive(pricing)
</script>

<template>
  <main class="w-full min-h-screen py-10 bg-slate-100 text-slate-900 dark:bg-slate-800 dark:text-slate-100">
    <div class="mb-8 px-4 text-right">
      <ToggleButton />
    </div>
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-5 px-6 m-auto max-w-full md:max-w-[1000px]">
      <PricingCard v-for="item in items"
        :name="item.name"
        :price="item.price"
        :description="item.description"
        :features="item.features"
        :key="item.name.toLowerCase()"
      />
    </div>
  </main>
</template>
