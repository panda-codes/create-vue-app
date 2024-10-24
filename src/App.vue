<script setup>
  import NavBar from './components/NavBar.vue';
  import Hero from './components/Hero.vue';
  import HomeCards from './components/HomeCards.vue';
  import JobListing from './components/JobListing.vue';
</script>

<template>
  <NavBar/>
  <Hero Title="Test Title" subtitle="Find the Vue job that fits your skills and needs"/>
  <HomeCards/>
  <JobListing/>
</template>

<style scoped></style>