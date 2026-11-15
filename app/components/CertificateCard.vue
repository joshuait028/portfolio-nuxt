<script setup lang="ts">
import type { Certificate } from '../types/certificate'

const props = defineProps<{
  certificate: Certificate
}>()

const emit = defineEmits<{
  view: [certificate: Certificate]
}>()
</script>

<template>
  <div class="cert-card">
    <button
      class="cert-image-button"
      type="button"
      :aria-label="`View ${props.certificate.name}`"
      @click="emit('view', props.certificate)"
    >
      <img
        :src="props.certificate.src"
        :alt="props.certificate.alt"
        class="cert-img"
      >
    </button>

    <p class="cert-name">
      {{ props.certificate.name }}
    </p>

    <a
      :href="props.certificate.verificationUrl"
      target="_blank"
      rel="noopener noreferrer"
      class="cert-link"
    >
      Verify Certificate Proof
    </a>
  </div>
</template>

<style scoped>
.cert-image-button {
  display: block;
  width: 100%;
  padding: 0;
  border: 0;
  background: transparent;
  cursor: zoom-in;
}
</style>
