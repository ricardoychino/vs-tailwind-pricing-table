<script setup>
import { useDark, useToggle } from '@vueuse/core'
import { SunIcon, MoonIcon } from '@heroicons/vue/24/outline'

const isDarkMode = useDark()
const toggleDark = useToggle(isDarkMode)
</script>

<template>
  <button @click="toggleDark()">
    <!-- Needs to include () - source: https://vueuse.org/shared/useToggle/#usetoggle -->
    <SunIcon class="toggle-icon" v-show="isDarkMode" />
    <MoonIcon class="toggle-icon" v-show="!isDarkMode" />
  </button>
</template>
