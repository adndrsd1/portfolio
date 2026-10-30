<script setup>
import { computed, ref, watch, nextTick, onMounted, onBeforeUnmount } from 'vue'
import profileImg from '../assets/adinda.jpg'
import imgBikeSharing from '../assets/projects/bike_data_analyst (1).png'
import imgBikeSharing2 from '../assets/projects/bike_data_analyst (2).png'
import imgBikeSharing3 from '../assets/projects/bike_data_analyst (3).png'
import imgFaceDetection from '../assets/projects/face_detection.png'
import imgHydroponic from '../assets/projects/hydroponic (1).png'
import imgHydroponic2 from '../assets/projects/hydroponic (2).png'
import imgHydroponic3 from '../assets/projects/hydroponic (3).png'
import imgHydroponic4 from '../assets/projects/hydroponic (4).png'
import imgHydroponic5 from '../assets/projects/hydroponic (5).png'
import imgHydroponic6 from '../assets/projects/hydroponic (6).png'
import imgHydroponic7 from '../assets/projects/hydroponic (7).png'
import imgMagang from '../assets/projects/magang (1).png'
import imgMagang2 from '../assets/projects/magang (2).png'
import imgMagang3 from '../assets/projects/magang (3).png'
import imgMagang4 from '../assets/projects/magang (4).png'
import imgMagang5 from '../assets/projects/magang (5).png'
import imgMagang6 from '../assets/projects/magang (6).png'
import imgMagang7 from '../assets/projects/magang (7).png'
import imgML from '../assets/projects/ml_automation (1).png'
import imgML2 from '../assets/projects/ml_automation (2).png'
import imgML3 from '../assets/projects/ml_automation (3).png'
import imgML4 from '../assets/projects/ml_automation (4).png'
import imgML5 from '../assets/projects/ml_automation (5).png'
import imgML6 from '../assets/projects/ml_automation (6).png'
import imgML7 from '../assets/projects/ml_automation (7).png'
import imgML8 from '../assets/projects/ml_automation (8).png'
import certBNSP from '../assets/certifications/bnsp.jpeg'
import certCertiport from '../assets/certifications/certiport.jpeg'
import certBelajarDasarDS from '../assets/certifications/belajar_dasar_DS.jpeg'
import certBelajarPengembanganML from '../assets/certifications/belajar_pengembangan_ML.jpeg'
import certDataClassification from '../assets/certifications/data_classification.jpeg'
import certDataFundamentals from '../assets/certifications/data_fundamental.jpeg'
import certIntroductionDS from '../assets/certifications/introduction_ds.jpeg'
import certPythonForDS from '../assets/certifications/python_for_ds.jpeg'
import certWadhwani from '../assets/certifications/wadhwani.png'
import certDigitalMarketing from '../assets/certifications/digital_marketing.jpeg'
import certMembangunSistemML from '../assets/certifications/membangun_sistem_ml.jpeg'

/* =========================================================
   PROFIL
   ========================================================= */

const showScrollTop = ref(false)

const sectionIds = ['home', 'about-me', 'projects', 'experiences', 'contact-me']

const updateActiveNav = () => {
  const atBottom =
  window.innerHeight + window.scrollY >= document.documentElement.scrollHeight - 4

  let current = sectionIds[0]
  if (atBottom) {
    current = sectionIds[sectionIds.length -1]
  } else {
    for (const id of sectionIds) {
      const el = document.getElementById(id)
      if (el && el.getBoundingClientRect().top <= 120) current = id
    }
  }

  document.querySelectorAll('.nav-menu a').forEach((a) => {
    const href = a.getAttribute('href') || ''
    const isCurrent =
      href.endsWith('#' + current) ||
      (current === 'home' && (href === '/' || href === '#'))
    a.classList.toggle('is-current', isCurrent)
  })
}

const onScroll = () => {
  const bottom = window.innerHeight + window.scrollY
  showScrollTop.value = bottom >= document.documentElement.scrollHeight - 200
  updateActiveNav()
}

const scrollToTop = () => window.scrollTo({ top: 0, behavior: 'smooth' })

const certifications = [
  {
    title: 'Certificate of Competence of Junior / Associate Data Scientist',
    issuer: 'Badan Nasional Sertifikasi Profesi (BNSP)',
    date: '2025-11',
    image: certBNSP,
    credentialId: '63112.2523.0000096.2025',
    url: ''
  },
  {
    title: 'Information Technology Specialist - Data Analytics',
    issuer: 'Certiport - Pearson VUE',
    date: '2024-12',
    image: certCertiport,
    credentialId: 'ewwK-4wvD',
    url: ''
  },
  {
    title: 'Belajar Dasar Data Science',
    issuer: 'Dicoding Indonesia',
    date: '2024-09',
    image: certBelajarDasarDS,
    credentialId: '1OP8WKRG1XQK',
    url: 'https://www.dicoding.com/certificates/1OP8WKRG1XQK'
  },
  {
    title: 'Belajar Pengembangan Machine Learning',
    issuer: 'Dicoding Indonesia',
    date: '2025-03',
    image: certBelajarPengembanganML,
    credentialId: '0LZ0RNOGRP65',
    url: 'https://www.dicoding.com/certificates/0LZ0RNOGRP65'
  },
  {
    title: 'Data Classification and Summarization Using IBM Granite',
    issuer: 'IBM',
    date: '2025-08',
    image: certDataClassification,
    credentialId: '4d4d7aa0-7291-4487-8b65-d7fd8d4db86a',
    url: 'https://www.credly.com/badges/4d4d7aa0-7291-4487-8b65-d7fd8d4db86a'
  },
  {
    title: 'Data Fundamentals',
    issuer: 'IBM',
    date: '2025-08',
    image: certDataFundamentals,
    credentialId: '88e7c533-a0dc-44fb-a81c-321309c36a3c',
    url: 'https://www.credly.com/badges/88e7c533-a0dc-44fb-a81c-321309c36a3c'
  },
  {
    title: 'Introduction to Data Science with Python',
    issuer: 'DQLab',
    date: '2024-07',
    image: certIntroductionDS,
    credentialId: '#DQLABINTP1IUSMVW',
    url: 'https://academy.dqlab.id/certificate/pdf/DQLABINTP1IUSMVW'
  },
  {
    title: 'Python Fundamental for Data Science',
    issuer: 'DQLab',
    date: '2024-08',
    image: certPythonForDS,
    credentialId: '#DQLABINTP1SNESJP',
    url: 'https://academy.dqlab.id/certificate/pdf/DQLABINTP1SNESJP'
  },
  {
    title: 'Meta Certified Digital Marketing Associate',
    issuer: 'Meta',
    date: '2025-12',
    image: certDigitalMarketing,
    credentialId: 'waLaQ-H98w',
    url: ''
  },
  {
    title: '21st Century Core Employability Skills',
    issuer: 'Wadhwani Foundation',
    date: '2023-05',
    image: certWadhwani,
    credentialId: '',
    url: ''
  },
  {
    title: 'Membangun Sistem Machine Learning',
    issuer: 'Dicoding Indonesia',
    date: '2026-05',
    image: certMembangunSistemML,
    credentialId: '81P2O6EKNZOY',
    url: 'https://www.dicoding.com/certificates/81P2O6EKNZOY'
  }
]

const formatCertDate = (value) => {
  if (!value) return ''
  if (!/^\d{4}-\d{2}$/.test(value)) return value
  return new Date(`${value}-01`).toLocaleDateString('en-US', {
    month: 'short',
    year: 'numeric'
  })
}

const certYear = (value) => value?.match(/\d{4}/)?.[0] ?? ''

const sortedCerts = computed(() =>
  [...certifications].sort((a, b) => b.date.localeCompare(a.date))
)

const showCerts = ref(false)
const certTrigger = ref(null)
const certClose = ref(null)

const openCerts = async () => {
  showCerts.value = true
  await nextTick()
  certClose.value?.focus()
}

const closeCerts = () => {
  showCerts.value = false
  certTrigger.value?.focus()
}


const onKeydown = (e) => {
  if (lightbox.value.open) {
    if (e.key === 'Escape') closeLightbox()
    else if (e.key === 'ArrowRight') lbNext()
    else if (e.key === 'ArrowLeft') lbPrev()
    return
  }
  if (e.key === 'Escape' && showCerts.value) closeCerts()
}

onMounted(() => {
  window.addEventListener('scroll', onScroll, { passive: true })
  window.addEventListener('keydown', onKeydown)
  onScroll()
})

onBeforeUnmount(() => {
  window.removeEventListener('scroll', onScroll)
  window.removeEventListener('keydown', onKeydown)
  document.body.style.overflow = ''
})
   
const profile = {
  name: 'Adinda Rizki Sya’bana Diva',
  role: 'Data & AI Engineer'
}
const year = new Date().getFullYear()

const heroBadges = [
  { label: 'Focus', wide: true, items: ['Data', 'Predictive Modeling', 'SQL', 'AI Engineer', 'Web Application'] },
  { label: 'Tools', items: ['Python', 'SQL', 'GitHub', 'Vue.js'] },
  { label: 'Based in', items: ['Jakarta, Indonesia'] }
]

const projects = [
  {
    title: 'Bike Sharing Data Analysis & Visualization',
    category: 'Personal Project',
    description: 'Bike sharing data visualization is a final project for course data analysis with Python submitted through Dicoding. This project aims discovering insight from bike sharing data with data analysis process, like loading data, preprocessing data, exploratory data analysis (EDA), visualization and explanatory analysis for get information to answer the business problems. ',
    tags: ['Python', 'Pandas', 'Streamlit'],
    images: [imgBikeSharing, imgBikeSharing2, imgBikeSharing3],
    link: [{ label: 'Source code', href: 'https://github.com/adndrsd1/Submission-Data-Bike-Sharing'}]
  },
  {
    title: 'Original Face Detection',
    category: 'Group Project',
    description: 'Original face detection is a project to create images classification model using CNN (Convolutional Neural Network) algorithm to recognize face image what an original face or fake face.',
    tags: ['AI', 'Computer Vision', 'Streamlit', 'TensorFlow', 'OpenCV'],
    images: imgFaceDetection,
    link: [{ label: 'Source code', href: 'https://github.com/adndrsd1/Project-Original-Face-Detection'}]
  },
  {
    title: 'Real-time Monitoring System Smart Hydroponic',
    category: 'Team Project',
    description: 'Smart Hydroponic Monitoring System is an IoT-based agricultural project developed to automate and optimize plant cultivation management. This project aims to monitor plant health and environmental conditions accurately through hardware-software integration, contributing to designing the layout of the smart hydroponic display, assembling IoT monitoring devices, developing the website-based interface for real-time plant tracking, and managing the backend logic flow.',
    tags: ['FastAPI', 'Vue.js', 'PostgreSQL', 'JWT', 'Docker', 'IoT'],
    images: [imgHydroponic, imgHydroponic2, imgHydroponic3, imgHydroponic4, imgHydroponic5, imgHydroponic6, imgHydroponic7],
    link: [{ label: 'Source code', href: 'https://github.com/ksm-aiot-upnvj/smart-hydroponic'}]
  },
  {
    title: 'Sistem Database Peraturan Pajak dan Retribusi Daerah',
    category: 'Team Project',
    description: 'Sistem Database Peraturan Pajak dan Retribusi Daerah is a backend-driven regulatory management platform developed to organize, store, and provide easy access to regional tax and retribution laws. This project aims to centralize legal documents and streamline information retrieval efficiently, contributing to backend development by processing regulatory data, setting up the database structure, managing business logic flows, and integrating them with the user interface.',
    tags: ['Django', 'Vue.js', 'PostgreSQL'],
    images: [imgMagang, imgMagang2, imgMagang3, imgMagang4, imgMagang5, imgMagang6, imgMagang7],
    link: [{ label: 'Source code', href: 'https://github.com/adndrsd1/D-sinkron'}]
  },
  {
    title: 'MLOps Pipeline for Reliable Machine Learning Systems',
    category: 'Personal Project',
    description: 'MLOps Pipeline for Reliable Machine Learning Systems is a project focused on implementing a robust, end-to-end machine learning workflow. This project aims to streamline model development, deployment, and maintenance in production environments, featuring continuous monitoring and an automated in real-time alerting mechanism via the Gmail API.',
    tags: ['Scikit-learn', 'MLFlow', 'Grafana', 'Prometheus', 'Docker', 'API Google'],
    images: [imgML, imgML2, imgML3, imgML4, imgML5, imgML6, imgML7, imgML8],
    link: [{ label: 'Source code', href: 'https://github.com/adndrsd1/Workflow-CI'}]
  },
]

const projectItems = computed(() =>
  projects.map((p) => ({
    ...p,
    gallery: [].concat(p.images ?? p.image ?? []).filter(Boolean),
    visibleLinks: [].concat(p.links ?? p.link ?? []).filter((l) => l?.href?.trim())
  }))
)

const slideIndex = ref(projects.map(() => 0))

const goSlide = (i, n) => {
  slideIndex.value[i] = n
}
const nextSlide = (i, total) => {
  slideIndex.value[i] = (slideIndex.value[i] + 1) % total
}
const prevSlide = (i, total) => {
  slideIndex.value[i] = (slideIndex.value[i] - 1 + total) % total
}

let touchStartX = 0
let justSwiped = false

const onTouchStart = (e) => {
  touchStartX = e.touches[0].clientX
}

const onTouchEnd = (e, i, total) => {
  if (total < 2) return
  const dx = e.changedTouches[0].clientX - touchStartX
  if (Math.abs(dx) < 40) return
  justSwiped = true          
  setTimeout(() => { justSwiped = false }, 300)
  if (dx < 0) nextSlide(i, total)
  else prevSlide(i, total)
}

const lightbox = ref({ open: false, project: 0, index: 0 })

const lbGallery = computed(() => projectItems.value[lightbox.value.project]?.gallery ?? [])
const lbTitle = computed(() => projectItems.value[lightbox.value.project]?.title ?? '')

const openLightbox = (i, n) => {
  if (justSwiped) return
  lightbox.value = { open: true, project: i, index: n }
}

const closeLightbox = () => {
  slideIndex.value[lightbox.value.project] = lightbox.value.index
  lightbox.value.open = false
}

const lbNext = () => {
  const total = lbGallery.value.length
  if (total) lightbox.value.index = (lightbox.value.index + 1) % total
}

const lbPrev = () => {
  const total = lbGallery.value.length
  if (total) lightbox.value.index = (lightbox.value.index - 1 + total) % total
}

const onLbTouchEnd = (e) => {
  if (lbGallery.value.length < 2) return
  const dx = e.changedTouches[0].clientX - touchStartX
  if (Math.abs(dx) < 40) return
  if (dx < 0) lbNext()
  else lbPrev()
}

watch(
  () => showCerts.value || lightbox.value.open,
  (locked) => {
    document.body.style.overflow = locked ? 'hidden' : ''
  }
)

const experiences = [
  {
    role: 'Head of Education Division in Academic Department',
    company: 'Himpunan Mahasiswa Informatika (HMIF) UPNVJ',
    type: 'Organization',
    period: 'February 2024 - January 2025',
    start: '2024-02',
    description: 'Organize event and collaborate with other member to share knowledge about learning materials in Informatics between students through a program named Kernel Session (Knowledge Exchange and Learning Session).',
    points: [],
    tags: ['Leadership', 'Teamwork', 'Communication', 'Public Speaking']
  },
  {
    role: 'Information Technology Intern as Web Developer',
    company: 'Kementerian Keuangan Republik Indonesia',
    type: 'Internship',
    period: 'March - July 2025',
    start: '2025-03',
    description: 'Develop a website for a database of legislation relating to regional tax regulations and regional levies using framework Django and Vue.js. ',
    points: [],
    tags: ['Web Development', 'Django', 'Vue.js', 'Database Management', 'Teamwork', 'Communication']
  },
  {
    role: 'Laboratory Teaching Assistant',
    company: 'Universitas Pembangunan Nasional Veteran Jakarta',
    type: 'Part-time',
    period: 'August - November 2025',
    start: '2025-08',
    description: 'Teaching the database practicum course for 1st semester Informatics students at the Faculty of Computer Science, Universitas Pembangunan Nasional Veteran Jakarta for the database fundamentals using DBMS tools, like MySQL and conducted practicum sessions actively.',
    points: [],
    tags: ['Teaching', 'Database Fundamentals', 'MySQL', 'DBMS', 'Communication']
  }
]

const sortedExperiences = computed(() =>
  [...experiences].sort((a, b) => b.start.localeCompare(a.start))
)

const skillGroups = [
  { label: 'Programming Languages', items: ['Python', 'JavaScript', 'TypeScript'] },
  { label: 'Framework & Libraries', items: ['Pandas', 'NumPy', 'Scikit-learn', 'TensorFlow', 'PyTorch', 'MLFlow', 'Streamlit', 'FastAPI', 'Django', 'Vue.js'] },
  { label: 'Databases', items: ['MySQL', 'PostgreSQL', 'MongoDB'] },
  { label: 'Infrastructure & Tools', items: ['Docker', 'Git', 'Visual Studio Code', 'Grafana', 'Prometheus', 'Cloud', 'Linux', 'Notion'] }
]

const education = [
  {
    degree: "Bachelor's Degree (S1) - Computer Science",
    school: "Universitas Pembangunan Nasional Veteran Jakarta",
    detail: "GPA: 3.92/4.00",
    timeframe: "AUGUST 2022 - JULY 2026"
  }
]

const interest = {
  text: 'I am passionate about turning complex data into actionable insights and building robust web applications, I thrive at the intersection of Data Science, AI, and Software Engineering. Throughout my academic journey, I have actively applied my skills across real-world projects. My technical expertise expanded through hands-on roles, including working on a web-based monitoring system project under faculty guidance and handling the development of institutional websites during my internship. With a solid foundation in data systems and web technologies, I am eager to embark on my career journey. Im looking to join a dynamic team in roles related to Data & AI Engineering where I can innovate, solve challenging problems, and add real value. '
}

const socials = [
  { label: 'LinkedIn', handle: 'linkedin.com/in/adinda-rizki-sya-bana-diva', href: 'https://www.linkedin.com/in/adinda-rizki-sya-bana-diva' },
  { label: 'GitHub', handle: 'github.com/adndrsd1', href: 'https://github.com/adndrsd1' },
  { label: 'Instagram', handle: '@adindarizki15', href: 'https://www.instagram.com/adindarizki15/' },
  { label: 'Email', handle: 'adindarizki15@gmail.com', href: 'mailto:adindarizki15@gmail.com' }
]

const socialLinks = socials.filter((item) => item.href)
const isWebLink = (href) => href.startsWith('http')
const socialText = (item) =>
  item.handle || item.href.replace(/^(https?:\/\/(www\.)?|mailto:)/, '').replace(/\/$/, '')
</script>

<template>
  <div class="portfolio-wrapper">
    <!-- Hero -->
    <section id="home" class="hero-section">
      <div class="container hero-content">
        <div class="hero-text">
          <h1>{{ profile.name }}</h1>
          <p class="hero-role">{{ profile.role }}</p>
          <dl class="hero-badges">
            <div v-for="group in heroBadges" :key="group.label" :class="['badge-card', { 'is-wide': group.wide }]">
              <dt>{{ group.label }}</dt>
              <dd>{{ group.items.join(' . ') }}</dd>
            </div>
          </dl>

          <div class="hero-actions">
            <a href="#projects" class="btn btn-primary">View Projects</a>
            <a href="#contact-me" class="btn btn-secondary">Contact Me</a>
          </div>
        </div>

        <div class="hero-visual">
          <img :src="profileImg" :alt="`Foto ${profile.name}`" class="hero-img" />
        </div>
      </div>
    </section>

    <!-- About Me -->
    <section id="about-me" class="section section-alt">
      <div class="container">
        <div class="section-title">
          <h2>About Me</h2>
          <p>Coming from an educational background and a high curiosity for technology</p>
        </div>

        <div class="about-grid">
          <div class="about-main">
            <p class="about-text" lang="en">{{ interest.text }}</p>
          </div>

          <aside class="about-side">
            <h3 class="side-title">Education</h3>

            <article v-for="edu in education" :key="edu.degree" class="edu-card">
              <div class="edu-head">
                <h4>{{ edu.degree }}</h4>
                <span class="edu-time">{{ edu.timeframe }}</span>
              </div>
              <p class="edu-school">{{ edu.school }}</p>
              <p class="edu-detail">{{ edu.detail }}</p>
              <p class="edu-link">
                <a href="https://pddikti.kemdiktisaintek.go.id/detail-mahasiswa/-_gICP7V7itBrx9SONTdf9Qsp3hzlsxBFq9hDmHIYOUO-fIxvBf8kvSb8aCJRYknE7dKGw==" target="_blank" rel="noopener">
                  Academic Record (PDDIKTI)
                </a>
              </p>
            </article>

            <button
              ref="certTrigger"
              class="cert-btn"
              type="button"
              aria-haspopup="dialog"
              @click="openCerts"
            >
              <svg class="cert-btn-icon" viewBox="0 0 24 24" aria-hidden="true">
                <circle cx="12" cy="8" r="6" />
                <path d="M15.477 12.89 17 22l-5-3-5 3 1.523-9.11" />
              </svg>
              <span>Certifications</span>
            </button>
          </aside>
        </div>
        <div class="skills-block">
          <h3 class="side-title">Technical Skills</h3>
          <div class="skills-card">
            <div v-for="group in skillGroups" :key="group.label" class="skill-row">
              <span class="skill-row-label">{{ group.label }}</span>
              <ul class="skill-badges">
                <li v-for="item in group.items" :key="item" class="skill-badge">{{ item }}</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects -->
    <section id="projects" class="section">
      <div class="container">
        <div class="section-title">
          <h2>Featured Projects</h2>
          <p>Implementation of knowledge as a real-world case study</p>
        </div>

        <div class="grid-projects">
          <article
            v-for="(project, i) in projectItems"
            :key="`${project.title}-${i}`"
            :class="['card', 'project-card', { 'is-featured': project.featured }]"
          >
            <div
              :class="['project-thumb', { 'is-contain': project.fit === 'contain' }]"
              role="group"
              aria-roledescription="carousel"
              :aria-label="`Gambar proyek ${project.title}`"
              @touchstart.passive="onTouchStart"
              @touchend.passive="onTouchEnd($event, i, project.gallery.length)"
            >
              <template v-if="project.gallery.length">
                <div
                  class="project-track"
                  :style="{ transform: `translateX(-${slideIndex[i] * 100}%)` }"
                >
                  <div v-for="(src, n) in project.gallery" :key="n" class="project-slide">
                    <!-- DIUBAH: gambar dibungkus <button> agar bisa diklik (dan diakses keyboard) -->
                    <button
                      class="project-zoom"
                      type="button"
                      :tabindex="slideIndex[i] === n ? 0 : -1"
                      :aria-label="`Perbesar gambar ${n + 1} proyek ${project.title}`"
                      @click="openLightbox(i, n)"
                    >
                      <img
                        :src="src"
                        :alt="`Tampilan proyek ${project.title} (${n + 1} dari ${project.gallery.length})`"
                        loading="lazy"
                      />
                    </button>
                  </div>
                </div>

                <template v-if="project.gallery.length > 1">
                  <button
                    class="project-nav prev"
                    type="button"
                    aria-label="Gambar sebelumnya"
                    @click="prevSlide(i, project.gallery.length)"
                  >
                    <svg class="theme-icon" viewBox="0 0 24 24" aria-hidden="true">
                      <path d="M15 18l-6-6 6-6" />
                    </svg>
                  </button>
                  <button
                    class="project-nav next"
                    type="button"
                    aria-label="Gambar berikutnya"
                    @click="nextSlide(i, project.gallery.length)"
                  >
                    <svg class="theme-icon" viewBox="0 0 24 24" aria-hidden="true">
                      <path d="M9 18l6-6-6-6" />
                    </svg>
                  </button>

                  <div class="project-dots">
                    <button
                      v-for="(_, n) in project.gallery"
                      :key="n"
                      type="button"
                      :class="['project-dot', { 'is-active': slideIndex[i] === n }]"
                      :aria-label="`Tampilkan gambar ${n + 1}`"
                      :aria-current="slideIndex[i] === n"
                      @click="goSlide(i, n)"
                    ></button>
                  </div>
                </template>
              </template>

              <span v-else class="project-thumb-fallback" aria-hidden="true">{{ project.category }}</span>
            </div>

            <div class="project-body">
              <span v-if="project.category" class="project-category">{{ project.category }}</span>

              <h3>{{ project.title }}</h3>
              <p class="project-desc">{{ project.description }}</p>

              <p v-if="project.highlight" class="project-highlight">{{ project.highlight }}</p>

              <div class="tag-group project-tags">
                <span v-for="tag in project.tags" :key="tag" class="tag">{{ tag }}</span>
              </div>

              <div v-if="project.visibleLinks.length" class="project-links">
                <a
                  v-for="link in project.visibleLinks"
                  :key="link.href"
                  :href="link.href"
                  target="_blank"
                  rel="noopener"
                >{{ link.label }} ↗</a>
              </div>
            </div>
          </article>
        </div>
      </div>
    </section>

    <!-- Experiences -->
    <section id="experiences" class="section section-alt">
      <div class="container">
        <div class="section-title">
          <h2>Experiences</h2>
          <p>A journey of learning and growth through real-world experiences</p>
        </div>

        <ol class="exp-timeline">
          <li v-for="exp in sortedExperiences" :key="exp.role + exp.company" class="exp-item">
            <!-- DITAMBAHKAN: kolom tahun besar di kiri (diambil dari field start) -->
            <div class="exp-year">
              <span class="exp-year-num">{{ exp.start.slice(0, 4) }}</span>
              <span v-if="exp.period !== exp.start.slice(0, 4)" class="exp-year-sub">{{ exp.period }}</span>
            </div>

            <div class="exp-content">
              <span v-if="exp.type" class="exp-type">{{ exp.type }}</span>

              <h3 class="exp-role">
                <a v-if="exp.url" :href="exp.url" target="_blank" rel="noopener">{{ exp.role }}</a>
                <template v-else>{{ exp.role }}</template>
              </h3>
              <p class="exp-company">{{ exp.company }}</p>

              <p v-if="exp.description" class="exp-desc">{{ exp.description }}</p>

              <ul v-if="exp.points?.length" class="exp-points">
                <li v-for="point in exp.points" :key="point">{{ point }}</li>
              </ul>

              <ul v-if="exp.tags?.length" class="exp-tags">
                <li v-for="tag in exp.tags" :key="tag" class="tag">{{ tag }}</li>
              </ul>
            </div>
          </li>
        </ol>
      </div>
    </section>

    <!-- Contact Me -->
    <section id="contact-me" class="section">
      <div class="container about-grid">
        <div class="about-main">
          <div class="section-title">
            <h2>Contact</h2>
            <p>Let's connect and collaborate!</p>
          </div>
          <section v-if="socialLinks.length" class="side-block">
            <ul class="social-list">
              <li v-for="item in socialLinks" :key="item.label">
                <span class="social-label">{{ item.label }}</span>
                <a
                :href="item.href"
                :target="isWebLink(item.href) ? '_blank' : null"
                :rel="isWebLink(item.href) ? 'noopener noreferrer' : null"
                >{{ socialText(item) }}</a>
              </li>
            </ul>
          </section>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
      <div class="container">
        <p>&copy; {{ year }} {{ profile.name }}. All rights reserved.</p>
      </div>
    </footer>

    <Transition name="fade-up">
      <button
        v-if="showScrollTop"
        class="scroll-top"
        type="button"
        aria-label="Kembali ke atas"
        @click="scrollToTop"
      >
        <svg class="theme-icon" viewBox="0 0 24 24" aria-hidden="true">
          <path d="M12 19V5M5 12l7-7 7 7" />
        </svg>
      </button>
    </Transition>

    <!-- Popup: Certifications -->
     <Teleport to="body">
      <Transition name="modal">
        <div v-if="showCerts" class="modal-backdrop" @click.self="closeCerts">
          <div
            class="modal"
            role="dialog"
            aria-modal="true"
            aria-labelledby="certs-title"
          >
            <div class="modal-head">
              <div>
                <h3 id="certs-title" class="modal-title">Certifications</h3>
                <p class="modal-sub">Program, workshop, and learning paths I have completed</p>
              </div>
              <button
                ref="certClose"
                class="modal-close"
                type="button"
                aria-label="Tutup"
                @click="closeCerts"
              >
                <svg class="theme-icon" viewBox="0 0 24 24" aria-hidden="true">
                  <path d="M6 6l12 12M18 6L6 18" />
                </svg>
              </button>
            </div>

            <ul class="modal-body cert-grid">
              <li v-for="cert in sortedCerts" :key="cert.title" class="cert-card">
                <div class="cert-media">
                  <a
                    v-if="cert.image"
                    :href="cert.image"
                    target="_blank"
                    rel="noopener"
                    :aria-label="`Buka gambar sertifikat ${cert.title}`"
                  >
                    <img :src="cert.image" :alt="`Sertifikat ${cert.title}`" loading="lazy" />
                  </a>
                  <!-- Pengganti kalau gambar belum ada -->
                  <span v-else class="cert-fallback" aria-hidden="true">{{ cert.issuer }}</span>

                  <span class="cert-chip">{{ certYear(cert.date) }}</span>
                </div>

                <div class="cert-body">
                  <h4 class="cert-title">{{ cert.title }}</h4>
                  <p class="cert-issuer">{{ cert.issuer }}</p>
                  <p class="cert-meta">
                    <span>Issued {{ formatCertDate(cert.date) }}</span>
                    <span v-if="cert.expires">Exp {{ formatCertDate(cert.expires) }}</span>
                  </p>
                  <p v-if="cert.credentialId" class="cert-id">ID: {{ cert.credentialId }}</p>
                  <a
                    v-if="cert.url"
                    :href="cert.url"
                    class="cert-link"
                    target="_blank"
                    rel="noopener"
                  >Verify certificate ↗</a>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </Transition>
    </Teleport>

    <Teleport to="body">
      <Transition name="lightbox">
        <div
          v-if="lightbox.open"
          class="lightbox"
          role="dialog"
          aria-modal="true"
          :aria-label="`Gambar proyek ${lbTitle}`"
          @click.self="closeLightbox"
          @touchstart.passive="onTouchStart"
          @touchend.passive="onLbTouchEnd"
        >
          <button class="lightbox-close" type="button" aria-label="Tutup" @click="closeLightbox">
            <svg class="theme-icon" viewBox="0 0 24 24" aria-hidden="true">
              <path d="M6 6l12 12M18 6L6 18" />
            </svg>
          </button>

          <template v-if="lbGallery.length > 1">
            <button class="lightbox-nav prev" type="button" aria-label="Gambar sebelumnya" @click="lbPrev">
              <svg class="theme-icon" viewBox="0 0 24 24" aria-hidden="true">
                <path d="M15 18l-6-6 6-6" />
              </svg>
            </button>
            <button class="lightbox-nav next" type="button" aria-label="Gambar berikutnya" @click="lbNext">
              <svg class="theme-icon" viewBox="0 0 24 24" aria-hidden="true">
                <path d="M9 18l6-6-6-6" />
              </svg>
            </button>
          </template>

          <figure class="lightbox-figure">
            <img
              :src="lbGallery[lightbox.index]"
              :alt="`${lbTitle} (${lightbox.index + 1} dari ${lbGallery.length})`"
            />
            <figcaption class="lightbox-caption">{{ lbTitle }}</figcaption>
          </figure>

          <span v-if="lbGallery.length > 1" class="lightbox-counter">
            {{ lightbox.index + 1 }} / {{ lbGallery.length }}
          </span>
        </div>
      </Transition>
    </Teleport>
  </div>
</template>