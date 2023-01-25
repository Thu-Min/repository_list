<template>
  <div class="home text-center">
    <repo-card class="mt-10"></repo-card>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import RepoCard from '../components/RepoCard.vue'

export default defineComponent({
  name: 'HomeView',
  components: {
    RepoCard
  },
});
</script>
