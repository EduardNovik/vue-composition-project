<script setup>
import { onMounted, reactive } from "vue";
import JobListing from "@/components/JobListing.vue";
import { RouterLink, useRoute } from "vue-router";
import PacmanLoader from "vue-spinner/src/PacmanLoader.vue";
import axios from "axios";

const router = useRoute();

const state = reactive({
  jobs: [],
  isLoading: true,
});

defineProps({
  limit: Number,
  showButton: {
    type: Boolean,
    default: false,
  },
});

onMounted(async () => {
  try {
    const response = await axios.get("/api/jobs");
    state.jobs = response.data;
  } catch (error) {
    console.log("Error fetching jobs", error);
  } finally {
    state.isLoading = false;
  }
});
</script>

<template>
  <section
    :class="[
      router.path === '/jobs' ? 'h-[calc(100vh-80px)]' : 'h-auto',
      'bg-blue-50',
      'px-4',
      'py-10',
    ]"
  >
    <div class="container-xl lg:container m-auto">
      <h2 class="text-3xl font-bold text-green-700 mb-6 text-center">
        Browse Jobs
      </h2>
      <!-- Show loading spinner while loading is true -->
      <div v-if="state.isLoading" class="flex justify-center py-6">
        <PacmanLoader />
      </div>
      <!-- Show job listing when done loading -->
      <div v-else class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <JobListing
          v-for="job of state.jobs.slice(0, limit || state.jobs.length)"
          :key="job.id"
          :job="job"
        />
      </div>
    </div>
  </section>

  <section v-if="showButton" class="m-auto max-w-lg my-10 px-6">
    <RouterLink
      to="/jobs"
      class="block bg-green-700 text-white text-center p-2 rounded-xl hover:bg-green-900 font-semibold text-xl"
      >View All Jobs</RouterLink
    >
  </section>
</template>
