<template>
  <div class="bg-main slidev-layout flex flex-col h-full">
    <div class="mt-auto mb-auto flex-grow">
      <slot />
    </div>
    <LayoutFooter
      :website="website"
      :hide-logo-in-corner="hideLogoInCorner"
    />
  </div>
</template>

<script setup lang="ts">
import LayoutFooter from '../components/LayoutFooter.vue'

defineProps({
  logoHeader: {
    type: String,
  },
  website: {
    type: String,
  },
  hideLogoInCorner: {
    type: Boolean,
  },
})
</script>