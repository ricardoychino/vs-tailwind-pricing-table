<script setup>
import { ref } from 'vue'
import { Bars3Icon, XMarkIcon } from '@heroicons/vue/24/outline'

defineProps(['menu'])

const menuOpen = ref(false)
</script>

<template>
  <button
    class="rounded-sm transition hover:!bg-gray-700 active:bg-gray-800 md:hidden"
    @click="menuOpen = !menuOpen"
  >
    <Bars3Icon v-show="!menuOpen" />
    <XMarkIcon v-show="menuOpen" />
  </button>
  <ul
    class="absolute left-0 right-0 top-full flex flex-col bg-gray-800 md:relative md:!flex md:flex-row md:gap-2"
    :class="{ hidden: !menuOpen }"
  >
    <li
      v-for="(menuItem, i) in menu"
      class="p-4 transition hover:!bg-gray-700 active:bg-gray-900 md:rounded-md md:py-2"
      :class="{ active: i == 0 }"
      :key="`menu-${menuItem.label}`"
    >
      <a :href="menuItem.route">{{ menuItem.label }}</a>
    </li>
  </ul>
</template>

<style scoped>
.active {
  @apply bg-gray-900;
}
</style>
