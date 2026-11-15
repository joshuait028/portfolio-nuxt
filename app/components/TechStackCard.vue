<script setup lang="ts">
defineProps<{
  name: string
  image: string
  alt: string
}>()
</script>

<template>
  <div class="tech-card">
    <img :src="image" :alt="alt">
    <p>{{ name }}</p>
  </div>
</template>
