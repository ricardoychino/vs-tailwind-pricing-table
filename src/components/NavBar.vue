<script setup>
import { ref } from 'vue'
import { menu, dropdown } from '@/menu.json'
import { BellIcon, Bars3Icon, XMarkIcon } from '@heroicons/vue/24/outline'
import ToggleButton from './ToggleButton.vue'

const menuOpen = ref(false)
const dropdownOpen = ref(false)
</script>

<template>
  <nav class="relative block bg-gray-800 text-slate-50">
    <div class="container mx-auto grid h-20 grid-cols-3 items-center gap-4 px-4 py-4 md:flex">
      <div class="order-2 mx-auto justify-self-center md:order-1 md:mx-0">
        <a href="javascript: void(0)">
          <img class="h-10" src="@/assets/logo.svg" alt="Logo" />
        </a>
      </div>

      <div class="order-1 flex">
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
      </div>

      <div class="order-3 flex items-center gap-1 justify-self-end md:ml-auto md:gap-2">
        <div class="flex items-center">
          <button>
            <BellIcon />
          </button>
          <ToggleButton />
        </div>
        <div class="relative">
          <a
            class="block h-8 w-8 overflow-hidden rounded-full"
            @click="dropdownOpen = !dropdownOpen"
          >
            <img src="@/assets/placeholder.jpg" alt="Profile picture" />
          </a>
          <ul
            class="absolute right-0 top-8 w-auto whitespace-nowrap rounded-md bg-slate-100 text-sm text-gray-700 shadow-md dark:bg-slate-700 dark:text-slate-100"
            v-show="dropdownOpen"
          >
            <li
              v-for="dropdownItem in dropdown"
              class="min-w-32 px-4 py-2"
              :key="`dropdown-${dropdownItem.label.toLowerCase()}`"
            >
              <a :href="dropdownItem.route">{{ dropdownItem.label }}</a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </nav>
</template>

<style scoped>
.active {
  @apply bg-gray-900;
}

:deep(svg) {
  @apply h-6 w-6 text-slate-400 transition hover:text-inherit active:text-inherit;
}
button {
  @apply p-1 md:p-2;
}
</style>
