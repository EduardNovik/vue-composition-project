<script setup>
import HomeCard from "@/components/HomeCard.vue";
import Hero from "@/components/Hero.vue";
import JobListings from "@/components/JobListings.vue";
</script>

<template>
  <!-- <Hero title="Test Title" subtitle="Test subtitle" /> -->
  <Hero />
  <HomeCard />
  <JobListings :limit="3" :showButton="true" />
</template>

<style></style>
