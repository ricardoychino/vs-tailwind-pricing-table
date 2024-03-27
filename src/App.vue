<script setup>
import { reactive } from 'vue'
import { pricing } from '@/pricing.json'
import PricingCard from '@/components/PricingCard.vue'
import NavBar from '@/components/NavBar.vue'
import ToggleButton from '@/components/ToggleButton.vue'

const items = reactive(pricing)
</script>

<template>
  <NavBar />
  <main
    class="min-h-screen w-full bg-slate-100 py-10 text-slate-900 dark:bg-slate-800 dark:text-slate-100"
  >
    <div class="mb-8 px-4 text-right">
      <ToggleButton />
    </div>
    <div
      class="m-auto grid max-w-full grid-cols-1 gap-5 px-6 sm:grid-cols-2 md:max-w-[1000px] md:grid-cols-3"
    >
      <PricingCard
        v-for="item in items"
        :name="item.name"
        :price="item.price"
        :description="item.description"
        :features="item.features"
        :key="item.name.toLowerCase()"
      />
    </div>
  </main>
</template>
