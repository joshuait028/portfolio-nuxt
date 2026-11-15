<script setup lang="ts">
definePageMeta({
  alias: '/tech-stack.html'
})

const technologies = [
  { name: 'HTML', image: '/images/html-logo.png', alt: 'HTML Logo' },
  { name: 'CSS', image: '/images/css-logo.png', alt: 'CSS Logo' },
  { name: 'JavaScript', image: '/images/javascript-logo.png', alt: 'JavaScript Logo' },
  { name: 'Java', image: '/images/java-logo.png', alt: 'Java Logo' },
  { name: 'SQL', image: '/images/mysql-logo.png', alt: 'MySQL Logo' },
  { name: 'Git', image: '/images/git-logo.png', alt: 'Git Logo' },
  { name: 'GitHub', image: '/images/github-logo.png', alt: 'GitHub Logo' },
  { name: 'VS Code', image: '/images/visual-studio-code-logo.png', alt: 'VS Code Logo' }
]
</script>

<template>
  <main class="tech">
    <h1>Tech-Stack</h1>

    <p class="tech-text">
      I use different programming languages and tools to build websites,
      systems, and practice software development. These are the technologies
      I am currently learning and working with.
    </p>

    <div class="tech-grid">
      <TechStackCard
        v-for="technology in technologies"
        :key="technology.name"
        :name="technology.name"
        :image="technology.image"
        :alt="technology.alt"
      />
    </div>
  </main>
</template>
