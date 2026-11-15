<script setup lang="ts">
definePageMeta({
  alias: '/contact-me.html'
})

useHead({
  title: 'Joshua Roy Arrogante | Contact'
})

useSeoMeta({
  description: 'Connect with Joshua Roy Arrogante through GitHub, Instagram, or LinkedIn. He is open to conversations and opportunities to learn.',
  ogTitle: 'Joshua Roy Arrogante | Contact',
  ogDescription: 'Connect with Joshua Roy Arrogante through GitHub, Instagram, or LinkedIn. He is open to conversations and opportunities to learn.',
  ogType: 'website',
  twitterCard: 'summary'
})
</script>

<template>
  <main class="contact-section">
    <p class="contact-label">CONTACT</p>

    <h1 class="contact-title">Get In Touch</h1>

    <p class="contact-text">
      Feel free to reach out anytime. Whether you have questions, or just
      want to connect — I'm always open to conversations and opportunities
      to learn.
    </p>

    <div class="contact-links">
      <ContactLink href="https://github.com/joshuait028" label="GitHub" />
      <ContactLink href="https://www.instagram.com/joshiedocchi/" label="Instagram" />
      <ContactLink href="https://www.linkedin.com/in/joshua-tolentino-22a031354/" label="LinkedIn" />
    </div>
  </main>
</template>
