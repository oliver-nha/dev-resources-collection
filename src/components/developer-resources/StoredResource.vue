
<script setup>
import LearningResource from "./LearningResource.vue";
defineProps(['resources']);
</script>

<template>
  <ul class="resources-list">
    <LearningResource
        v-for="resource in resources"
        :key="resource.id"
        :id="resource.id"
        :title="resource.title"
        :description="resource.description"
        :link="resource.link"
    />
  </ul>
</template>

<style scoped>
.resources-list {
  list-style: none;
  margin: 0;
  padding: 0 1rem;
  max-width: 48rem;
  margin: auto;
}
</style>
