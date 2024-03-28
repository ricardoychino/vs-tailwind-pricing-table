<script setup>
import { ref } from 'vue'

defineProps(['menu'])

const dropdownOpen = ref(false)
</script>

<template>
  <div class="relative">
    <a
      class="block h-8 w-8 overflow-hidden rounded-full ring-2 ring-white ring-offset-2 ring-offset-gray-800"
      @click="dropdownOpen = !dropdownOpen"
    >
      <img src="@/assets/placeholder.jpg" alt="Profile picture" />
    </a>
    <ul
      class="absolute right-0 top-9 w-auto overflow-hidden whitespace-nowrap rounded-md bg-slate-100 text-sm text-gray-700 shadow-md dark:bg-slate-700 dark:text-slate-100"
      v-show="dropdownOpen"
    >
      <li
        v-for="dropdownItem in menu"
        class="min-w-32"
        :key="`dropdown-${dropdownItem.label.toLowerCase()}`"
      >
        <a
          :href="dropdownItem.route"
          class="block w-full px-4 py-2 hover:bg-slate-300 dark:hover:bg-slate-600"
          >{{ dropdownItem.label }}</a
        >
      </li>
    </ul>
  </div>
</template>
