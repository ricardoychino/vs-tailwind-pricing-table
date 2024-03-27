<script setup>
import { reactive } from "vue";
import { pricing } from "@/pricing.json"
import PricingCard from "@/components/PricingCard.vue"

const items = reactive(pricing)
</script>

<template>
  <main class="w-[100vw] min-h-[100vh] py-10 bg-slate-100">
    <div class="mb-8">
      <button>
        Toggle mode
      </button>
    </div>
    <div class="flex flex-wrap justify-center gap-5 m-auto">
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
