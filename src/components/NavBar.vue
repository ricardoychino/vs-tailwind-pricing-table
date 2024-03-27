<script setup>
import { menu, dropdown } from '@/menu.json'
import { BellIcon } from '@heroicons/vue/24/outline'
import ToggleButton from '@/components/ToggleButton.vue'
import NavMenu from '@/components/navbar/NavMenu.vue'
import ProfileMenu from '@/components/navbar/ProfileMenu.vue'
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
        <NavMenu :menu="menu" />
      </div>

      <div class="order-3 flex items-center gap-1 justify-self-end md:ml-auto md:gap-2">
        <div class="flex items-center">
          <button>
            <BellIcon />
          </button>
          <ToggleButton />
        </div>

        <ProfileMenu :menu="dropdown" />
      </div>
    </div>
  </nav>
</template>

<style scoped>
:deep(svg) {
  @apply h-6 w-6 text-slate-400 transition hover:text-inherit active:text-inherit;
}
button {
  @apply p-1 md:p-2;
}
</style>
