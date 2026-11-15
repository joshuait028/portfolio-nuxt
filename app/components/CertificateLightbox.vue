<script setup lang="ts">
import type { Certificate } from '../types/certificate'

defineProps<{
  certificate: Certificate
}>()

const emit = defineEmits<{
  close: []
}>()
</script>

<template>
  <div
    class="lightbox active"
    role="dialog"
    aria-modal="true"
    :aria-label="certificate.title"
    @click="emit('close')"
  >
    <div class="lightbox-content" @click.stop>
      <button
        class="lightbox-close"
        type="button"
        aria-label="Close certificate"
        @click="emit('close')"
      >
        <i class="fa-solid fa-xmark" aria-hidden="true"></i>
      </button>

      <img :src="certificate.src" :alt="certificate.alt">
      <p>{{ certificate.title }}</p>
    </div>
  </div>
</template>
