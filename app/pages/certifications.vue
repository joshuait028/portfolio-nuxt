<script setup lang="ts">
import type { Certificate } from '../types/certificate'

definePageMeta({
  alias: '/certifications.html'
})

interface SweetAlertToastOptions {
  toast: true
  position: 'top-end'
  icon: 'info'
  title: string
  showConfirmButton: false
  timer: number
  timerProgressBar: true
}

interface SweetAlert {
  fire(options: SweetAlertToastOptions): void
}

interface SweetAlertWindow extends Window {
  Swal?: SweetAlert
}

useHead({
  title: 'Joshua Roy Arrogante | Certifications',
  link: [
    {
      rel: 'stylesheet',
      href: 'https://cdn.jsdelivr.net/npm/sweetalert2@11/dist/sweetalert2.min.css'
    },
    {
      rel: 'stylesheet',
      href: 'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css'
    }
  ],
  script: [
    {
      src: 'https://cdn.jsdelivr.net/npm/sweetalert2@11',
      defer: true
    }
  ]
})

useSeoMeta({
  description: 'Explore certificates earned by Joshua Roy Arrogante while learning technology and programming, including Microsoft Word, Java programming, and modern databases.',
  ogTitle: 'Joshua Roy Arrogante | Certifications',
  ogDescription: 'Explore certificates earned by Joshua Roy Arrogante while learning technology and programming, including Microsoft Word, Java programming, and modern databases.',
  ogType: 'website',
  twitterCard: 'summary'
})

const certificates: Certificate[] = [
  {
    src: '/images/arrogante-word-cert.png',
    alt: 'Word Certificate',
    name: 'Microsoft Word Certificate',
    title: 'Word MS',
    verificationUrl: 'https://www.certiport.com/portal/pages/credentialverification.aspx'
  },
  {
    src: '/images/arrogante-java-cert.png',
    alt: 'Java Certificate',
    name: 'Java Programming Certificate',
    title: 'Java Programming',
    verificationUrl: 'https://www.certiport.com/portal/pages/credentialverification.aspx'
  },
  {
    src: '/images/arrogante-certification-saylor-modern-database.jpg',
    alt: 'Modern Database Certificate',
    name: 'Modern Database Certif9icate',
    title: 'Modern Database Programming',
    verificationUrl: 'https://learn.saylor.org/admin/tool/certificate/index.php'
  }
]

const activeCertificate = ref<Certificate | null>(null)

function openLightbox(certificate: Certificate) {
  activeCertificate.value = certificate

  const sweetAlert = (window as SweetAlertWindow).Swal
  if (!sweetAlert) {
    throw new Error('SweetAlert2 failed to load.')
  }

  sweetAlert.fire({
    toast: true,
    position: 'top-end',
    icon: 'info',
    title: `Viewing: ${certificate.title}`,
    showConfirmButton: false,
    timer: 1500,
    timerProgressBar: true
  })
}

function closeLightbox() {
  activeCertificate.value = null
}

function handleKeydown(event: KeyboardEvent) {
  if (event.key === 'Escape') {
    closeLightbox()
  }
}

onMounted(() => {
  window.addEventListener('keydown', handleKeydown)
})

onUnmounted(() => {
  window.removeEventListener('keydown', handleKeydown)
})
</script>

<template>
  <main class="cert-section">
    <p class="cert-label">
      CERTIFICATIONS
    </p>

    <h1 class="cert-title">
      My Certificates
    </h1>

    <p class="cert-text">
      These are some of the certifications and achievements
      I earned while learning technology and programming.
    </p>

    <div class="cert-grid">
      <CertificateCard
        v-for="certificate in certificates"
        :key="certificate.src"
        :certificate="certificate"
        @view="openLightbox"
      />
    </div>

    <CertificateLightbox
      v-if="activeCertificate"
      :certificate="activeCertificate"
      @close="closeLightbox"
    />
  </main>
</template>
