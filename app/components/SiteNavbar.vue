<script setup lang="ts">
const route = useRoute()
const isMenuOpen = ref(false)

const navigationItems = [
  { label: 'Home', to: '/' },
  { label: 'About', to: '/about-me.html' },
  { label: 'Tech Stack', to: '/tech-stack.html' },
  { label: 'Certifications', to: '/certifications.html' },
  { label: 'Contact Me', to: '/contact-me.html' }
]

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
  <nav class="navbar bg-base-100 shadow-sm" role="navigation" aria-label="main navigation">
    <div class="flex-1 navbar-brand">
      <NuxtLink class="navbar-item" to="/" aria-label="Joshua Arrogante home">
        <img
          src="/images/arrogante-website-logo.svg"
          alt="Logo"
          :class="{ 'is-large': largeLogo }"
        >
      </NuxtLink>
    </div>

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

    <div
      class="flex-none navbar-menu"
      id="navbarMenu"
      :class="{ 'is-active': isMenuOpen }"
    >
      <ul class="menu menu-horizontal">
        <li v-for="item in navigationItems" :key="item.to">
          <NuxtLink
            :class="[
              item.to === '/contact-me.html'
                ? 'button is-primary navbar-item'
                : 'navbar-item',
              { 'is-active': isActive(item.to) }
            ]"
            :to="item.to"
            :aria-current="isActive(item.to) ? 'page' : undefined"
            @click="closeMenu"
          >
            {{ item.label }}
          </NuxtLink>
        </li>
      </ul>
    </div>
  </nav>
</template>
