<script setup>
import { useDark, useToggle } from "@vueuse/core";
import { SunIcon, MoonIcon } from "@heroicons/vue/24/solid"

const isDarkMode = useDark()
const toggleDark = useToggle(isDarkMode)
</script>

<template>
  <button 
    class="p-1 rounded-md bg-slate-300 text-slate-800"
    @click="toggleDark()"><!-- Needs to include () - source: https://vueuse.org/shared/useToggle/#usetoggle -->
    <SunIcon class="toggle-icon" v-show="isDarkMode" />
    <MoonIcon class="toggle-icon" v-show="!isDarkMode" />
  </button>
</template>

<style scoped>
.toggle-icon {
  @apply h-7 w-7;
}
</style>