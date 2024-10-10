<script setup>
import Navbar from "@/components/Navbar.vue";
import HomeCard from "@/components/HomeCard.vue";
import Hero from "@/components/Hero.vue";
import JobListings from "@/components/JobListings.vue";
</script>

<template>
  <Navbar />
  <Hero title="Test Title" subtitle="Test subtitle" />
  <HomeCard />
  <JobListings :limit="3" :showButton="true" />
</template>

<style scoped></style>

<!-- Use : when you want to pass non-string values, such as numbers, booleans, arrays, objects, or expressions.
No : needed for plain string values. -->
