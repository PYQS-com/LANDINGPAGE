<script setup lang="ts">
import Navbar from "./components/Navbar.vue";
import Hero from "./components/Hero.vue";
import TabFeatures from "./components/TabFeatures.vue";
import Sponsors from "./components/Sponsors.vue";
import Community from "./components/Community.vue";
import Contact from "./components/Contact.vue";
import FAQ from "./components/FAQ.vue";
import Footer from "./components/Footer.vue";
import ReviewsMarquee from '@/components/ReviewsMarquee.vue';
// import Header from "./components/Header.vue";
import SmoothCursor from "./components/magicui/SmoothCursor.vue";
</script>

<template>
  <div class="relative">
    <!-- <Header /> -->
    <main>
      <Navbar />
      <Hero />
      <Sponsors />
      <!-- <Benefits />
      <Features /> -->
      <!-- <Services /> -->
      <TabFeatures />
      <!-- <ReviewsMarquee /> -->
      <!-- <Pricing /> -->
      <!-- <Testimonials /> -->
      <!-- <Team /> -->
      <Community />
      <Contact />
      <FAQ />
    </main>
    <Footer />
    <SmoothCursor /> <!-- Add this component -->
  </div>
</template>
