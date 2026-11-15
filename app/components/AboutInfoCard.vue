<script setup lang="ts">
withDefaults(defineProps<{
  label: string
  title: string
  wide?: boolean
}>(), {
  wide: false
})
</script>

<template>
  <div class="about-card" :class="{ 'wide-card': wide }">
    <span class="mini-label">{{ label }}</span>
    <h2>{{ title }}</h2>
    <slot />
  </div>
</template>
