<script setup lang="ts">
import type { NuxtError } from '#app'

const props = defineProps<{
  error: NuxtError
}>()

const statusCode = computed(() => props.error.statusCode ?? 500)
const isNotFound = computed(() => statusCode.value === 404)
const title = computed(() =>
  isNotFound.value ? 'Page Not Found' : 'Something went wrong'
)
const description = computed(() =>
  isNotFound.value
    ? 'The page you’re looking for doesn’t exist or may have moved.'
    : 'An unexpected error occurred. Please try again or return to the homepage.'
)

useHead(() => ({
  title: `${statusCode.value} | ${title.value}`
}))

function goHome() {
  clearError({ redirect: '/' })
}
</script>

<template>
  <div>
    <SiteNavbar />

    <main class="error-section">
      <p class="error-code" aria-label="Error status code">
        {{ statusCode }}
      </p>
      <h1 class="error-title">
        {{ title }}
      </h1>
      <p class="error-description">
        {{ description }}
      </p>
      <button class="home-button error-home-button" type="button" @click="goHome">
        Back to Home
      </button>
    </main>

    <SiteFooter />
  </div>
</template>

<style scoped>
.error-section {
  min-height: 600px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 80px 24px;
  text-align: center;
}

.error-code {
  margin-bottom: 24px;
  color: #fff;
  font-family: 'Syne', sans-serif;
  font-size: clamp(5rem, 16vw, 9rem);
  font-weight: 800;
  letter-spacing: -0.08em;
  line-height: 0.9;
}

.error-title {
  margin-bottom: 16px;
  font-family: 'Syne', sans-serif;
  font-size: clamp(2rem, 5vw, 3rem);
}

.error-description {
  max-width: 600px;
  margin-bottom: 32px;
  color: #8f8f8f;
  line-height: 1.8;
}

.error-home-button {
  font: inherit;
  cursor: pointer;
}
</style>
