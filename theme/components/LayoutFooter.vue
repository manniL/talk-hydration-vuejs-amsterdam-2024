<script setup lang="ts">
import { computed } from 'vue'
// @ts-ignore
import { isDark } from '@slidev/client/logic/dark.ts'

defineProps({
  website: {
    type: String,
  },
  hideLogoInCorner: {
    type: Boolean
  }
})

const imgPrefix = computed(() => isDark.value ? 'white' : 'black')
const img = computed(() => `https://raw.githubusercontent.com/manniL/lichter.io/main/public/img/logo/glyph-and-word-${imgPrefix.value}-colored.svg`)
</script>

<template>
  <footer class="flex flex-col justify-between w-full mt-auto text-black dark:text-white">
    <div class="flex justify-between w-full dark:text-white">
      <a :href="website || $slidev.configs.website" class="border-b-0!">
        <img v-show="!hideLogoInCorner && !$slidev.configs.hideLogoInCorner" class="w-10 h-10" :src="img" />
      </a>
      <span>{{ $slidev.nav.currentPage }}</span>
    </div>
  </footer>
</template>