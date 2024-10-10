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

<!-- <JobListings :limit="3" :showButton="true" /> -->
<!-- Use : when you want to pass non-string values, such as numbers, booleans, arrays, objects, or expressions.
No : needed for plain string values. -->
