<script setup lang="ts">
const route = useRoute()
const isMenuOpen = ref(false)

const navigationItems = computed(() => {
  const home = { label: 'Home', to: '/' }
  const about = { label: 'About', to: '/about-me.html' }
  const certifications = { label: 'Certifications', to: '/certifications.html' }
  const techStack = { label: 'Tech Stack', to: '/tech-stack.html' }

  return route.path === '/tech-stack.html'
    ? [home, about, techStack, certifications]
    : [home, about, certifications, techStack]
})

const contactLabel = computed(() =>
  route.path === '/contact-me.html' ? 'Contact Me' : 'Contact'
)

const largeLogo = computed(() =>
  route.path === '/' || route.path === '/tech-stack.html'
)

function isActive(to: string) {
  return route.path === to
}

function closeMenu() {
  isMenuOpen.value = false
}

watch(() => route.path, closeMenu)
</script>

<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <NuxtLink class="navbar-item" to="/" aria-label="Joshua Arrogante home">
        <img
          src="/images/arrogante-website-logo.svg"
          alt="Logo"
          :class="{ 'is-large': largeLogo }"
        >
      </NuxtLink>

      <button
        class="navbar-burger"
        :class="{ 'is-active': isMenuOpen }"
        type="button"
        :aria-expanded="isMenuOpen"
        aria-controls="navbarMenu"
        :aria-label="isMenuOpen ? 'Close navigation menu' : 'Open navigation menu'"
        @click="isMenuOpen = !isMenuOpen"
      >
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </button>
    </div>

    <div
      id="navbarMenu"
      class="navbar-menu"
      :class="{ 'is-active': isMenuOpen }"
    >
      <div class="navbar-start"></div>

      <div class="navbar-end">
        <NuxtLink
          v-for="item in navigationItems"
          :key="item.to"
          class="navbar-item"
          :class="{ 'is-active': isActive(item.to) }"
          :to="item.to"
          @click="closeMenu"
        >
          {{ item.label }}
        </NuxtLink>

        <div class="navbar-item">
          <NuxtLink
            class="button is-primary"
            :class="{ 'is-active': isActive('/contact-me.html') }"
            to="/contact-me.html"
            @click="closeMenu"
          >
            <strong>{{ contactLabel }}</strong>
          </NuxtLink>
        </div>
      </div>
    </div>
  </nav>
</template>
