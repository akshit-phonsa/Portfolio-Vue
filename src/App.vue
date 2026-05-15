<template>
  <div>
    <!-- Show spinner while initial loading -->
    <div v-if="loading" >
      <LoadingSpinner />
    </div>

    <!-- Main app -->
    <div v-else class="min-h-screen bg-linear-to-br from-gray-900 via-purple-950 to-gray-900">
      <Navbar />
      <Hero />
      <Service />
      <About />
      <ExperienceAndSkills />
      <Projects />
      <Certifications />
      <Contact />
      <Testimonials />
      <Footer />
      <BackToTop />
    </div>
  </div>
</template>

<script>
import { defineComponent, ref, onMounted, nextTick } from 'vue';
import AOS from 'aos';
import 'aos/dist/aos.css';

import Navbar from './components/Navbar.vue';
import Hero from './components/Hero.vue';
import Service from './components/Service.vue';
import About from './components/About.vue';
import ExperienceAndSkills from './components/ExperienceAndSkills.vue';
import Projects from './components/Projects.vue';
import Certifications from './components/Certifications.vue';
import Contact from './components/Contact.vue';
import Testimonials from './components/Testimonials.vue';
import Footer from './components/Footer.vue';
import BackToTop from './components/BackToTop.vue';
import LoadingSpinner from './components/LoadingSpinner.vue';

export default defineComponent({
  name: 'App',
  components: {
    Navbar,
    Hero,
    Service,
    About,
    ExperienceAndSkills,
    Projects,
    Certifications,
    Contact,
    Testimonials,
    Footer,
    BackToTop,
    LoadingSpinner
  },
  setup() {
    const loading = ref(true);

    onMounted(async () => {
      // Optional: wait nextTick so DOM renders
      await nextTick();

      AOS.init({
        duration: 800,
        once: false,
        offset: 100,
        easing: 'ease-in-out',
      });

      setTimeout(() => {
        loading.value = false;
      }, 800);
    });

    return { loading };
  }
});
</script>