<script setup>
import Navbar from './components/Navbar.vue';
</script>
<template>
  <div>
    <NuxtRouteAnnouncer />
    <navbar />
    <NuxtPage /> <!-- Use NuxtPage em vez de NuxtWelcome -->
  </div>
</template>
