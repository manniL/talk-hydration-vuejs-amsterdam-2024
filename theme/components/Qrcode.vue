<script setup lang="ts">
import { useQRCode } from '@vueuse/integrations/useQRCode'

const props = defineProps<{
  url: string,
  note?: string
}>()

const qrcode = useQRCode(props.url, {
  errorCorrectionLevel: 'H',
  margin: 3,
})
</script>

<template>
  <div class="flex flex-col items-center justify-center">
    <img v-if="url" class="mt-6 mb-2 rounded border" :src="qrcode" :alt="`QR Code to ${url}`">
    <p v-if="note">{{ note }}</p>
  </div>
</template>