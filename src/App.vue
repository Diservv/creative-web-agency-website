<template>
  <div class="min-h-screen bg-gradient-to-b from-gray-50 to-gray-100">
    <Navbar />
    <Home />
    <Footer />
  </div>
</template>

<script setup>
import Navbar from '@/components/Navbar.vue';
import Footer from '@/components/Footer.vue';
import Home from '@/views/Home.vue';
</script>