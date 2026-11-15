<script setup lang="ts">
const route = useRoute()

const footerText = computed(() =>
  route.path === '/certifications.html'
    ? 'Joshua Roy Arrogante • © 2026'
    : 'Joshua Arrogante • @ 2026'
)
</script>

<template>
  <footer class="footer">
    {{ footerText }}
  </footer>
</template>
