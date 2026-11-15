<script setup lang="ts">
defineProps<{
  href: string
  label: string
}>()
</script>

<template>
  <a
    :href="href"
    target="_blank"
    rel="noopener noreferrer"
    class="contact-button"
  >
    {{ label }}
  </a>
</template>
