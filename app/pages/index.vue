<template>
  <main class="home-section">
    <div class="profile-container">
      <img
        src="/images/arrogante-website-profile.png"
        alt="Joshua Picture"
        class="profile-image"
      >
    </div>

    <h1 class="home-title">
      Joshua Roy Arrogante
    </h1>

    <p class="home-text">
      An Aspiring Web Developer.
    </p>

    <div class="home-buttons">
      <NuxtLink to="/about-me.html" class="home-button">
        About
      </NuxtLink>
      <NuxtLink to="/tech-stack.html" class="home-button">
        Tech Stack
      </NuxtLink>
      <NuxtLink to="/certifications.html" class="home-button">
        Certifications
      </NuxtLink>
      <NuxtLink to="/contact-me.html" class="home-button">
        Contact
      </NuxtLink>
    </div>
  </main>
</template>
