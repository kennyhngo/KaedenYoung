<script setup lang="ts">
import AboutMe from "./components/AboutMe.vue";
import Contact from "./components/Contact.vue";
import Features from "./components/Features.vue";
import Footer from "./components/Footer.vue";
import Hero from "./components/Hero.vue";
import Navbar from "./components/Navbar.vue";
import Pricing from "./components/Pricing.vue";
import Testimonials from "./components/Testimonials.vue";

import { Toaster } from 'vue-sonner';
import 'vue-sonner/style.css';
</script>

<template>
  <Toaster richColors />
  <Navbar />
  <Hero />
  <!-- <Sponsors /> -->
  <!-- <Benefits /> -->
  <AboutMe />
  <Features />
  <!-- <Services /> -->
  <!-- <HowItWorks /> -->
  <!-- <Testimonials /> -->
  <!-- <Team /> -->
  <!-- <Community /> -->
  <Pricing />
  <Testimonials />
  <Contact />
  <!-- <FAQ /> -->
  <Footer />
</template>
