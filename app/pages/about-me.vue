<script setup lang="ts">
definePageMeta({
  alias: '/about-me.html'
})

useHead({
  title: 'Joshua Roy Arrogante | About'
})

useSeoMeta({
  description: 'Learn about Joshua Roy Arrogante, a BSIT student at St. Dominic College of Asia, his career goals in networking and web development, and his interests.',
  ogTitle: 'Joshua Roy Arrogante | About',
  ogDescription: 'Learn about Joshua Roy Arrogante, a BSIT student at St. Dominic College of Asia, his career goals in networking and web development, and his interests.',
  ogType: 'website',
  twitterCard: 'summary'
})
</script>

<template>
  <main class="about-wrapper">
    <section class="intro-section">
      <h1 class="main-title">About Me</h1>

      <p class="intro-text">
        Aspiring developer dedicated to learning and improving in the field
        of programming. A BSIT student of St. Dominic College of Asia with
        a passion for technology and a drive to create innovative solutions
        to modern problems.
      </p>
    </section>

    <section class="about-grid">
      <AboutInfoCard label="INTRODUCTION" title="Hello, I'm Joshua Arrogante 👋" wide>
        <p>
          I am Joshua Roy Arrogante, 20 years old, born on February 15,
          2006. I am an easy-going person and I am always open to learning
          new things. I enjoy doing my hobbies in my free time and I am
          dedicated to improving myself every day while staying true to my
          goals and being positive and God-centered in everything I do.
        </p>
      </AboutInfoCard>

      <AboutInfoCard label="Professional Aspirations" title="Career Goals">
        <p>
          As an Information Technology student, I aspire to build a
          successful career in both networking and web development. I aim
          to develop secure and efficient network systems while also
          creating responsive and user-friendly websites that solve
          real-world problems. Through continuous learning and hands-on
          experience, I hope to become a skilled IT professional who can
          contribute to the growth of businesses and technology.
        </p>
      </AboutInfoCard>

      <AboutInfoCard label="Hobbies" title="Hobbies">
        <div class="tag-container">
          <span class="tag-item">Gaming</span>
          <span class="tag-item">Long Rides/Travelling</span>
          <span class="tag-item">Cooking</span>
          <span class="tag-item">Reading</span>
          <span class="tag-item">Working Out</span>
        </div>
      </AboutInfoCard>
    </section>
  </main>
</template>
