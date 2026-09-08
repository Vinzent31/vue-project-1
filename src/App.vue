<script setup>
import { onMounted } from 'vue'
import AOS from 'aos'
import 'aos/dist/aos.css'

import Navbar from './components/navbar.vue'
import Hero from './components/hero.vue'
import Starter from './components/starter.vue'
import About from './components/aboutworld.vue'
import Gameplay from './components/gameplay.vue'
import Footer from './components/footer.vue'

onMounted(() => {
  AOS.init({
    duration: 800,   // Durasi animasi (ms)
    once: true,       // Animasi hanya berjalan 1x saat di-scroll
    easing: 'ease-out-cubic', // Transisi yang halus
    offset: 100,      // Jarak pemicu animasi dari bawah layar
  })
})
</script>

<template>
  <div class="relative min-h-screen overflow-hidden bg-[#001b16] text-white">

    <div
      class="pointer-events-none fixed inset-0 z-0 opacity-[0.07]"
      style="
        background-image:
          linear-gradient(rgba(16,185,129,0.35) 1px, transparent 1px),
          linear-gradient(90deg, rgba(16,185,129,0.35) 1px, transparent 1px);
        background-size: 64px 64px;
      "
    ></div>

    <div
      class="pointer-events-none fixed left-1/2 top-1/2
             z-0 h-[700px] w-[700px]
             -translate-x-1/2 -translate-y-1/2
             rounded-full
             bg-emerald-500/[0.06]
             blur-[140px]"
    ></div>

    <div class="relative z-10">
      <Navbar />

      <main id="home">
        <Hero data-aos="fade-up" data-aos-duration="1000" />

        <section data-aos="fade-up" id="about">
          <About />
        </section>

        <section data-aos="fade-up"  id="starters">
          <Starter />
        </section>

        <section data-aos="fade-up"  id="gameplay">
          <Gameplay />
        </section>

        <section data-aos="fade-up">
          <Footer />
        </section>
      </main>
    </div>
  </div>
</template>