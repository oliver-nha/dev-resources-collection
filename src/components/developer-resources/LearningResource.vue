<script setup>
import BaseButton from "@/components/UI/BaseButton.vue";

defineProps(['id', 'title', 'description', 'link']);
</script>

<template>
  <li class="resource-item">
    <base-card>
      <div class="resource-header">
        <h3>{{ title }}</h3>
        <base-button mode="flat">
          <span class="btn-text">Delete</span>
        </base-button>
      </div>
      <p class="description">{{ description }}</p>
      <nav class="resource-nav">
        <a :href="link" target="_blank" rel="noopener noreferrer">
          View Resource
          <span class="arrow">→</span>
        </a>
      </nav>
    </base-card>
  </li>
</template>

<style scoped>
.resource-item {
  margin: 2rem auto;
  max-width: 48rem;
  transition: transform 0.2s ease;
}

.resource-item:hover {
  transform: translateY(-2px);
}

.resource-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-bottom: 1rem;
  border-bottom: 1px solid #e5e7eb;
}

h3 {
  font-size: 1.5rem;
  font-weight: 600;
  color: #111827;
  margin: 0;
}

.description {
  margin: 1rem 0;
  color: #4b5563;
  line-height: 1.5;
}

.resource-nav {
  margin-top: 1.5rem;
}

.resource-nav a {
  text-decoration: none;
  color: #2563eb;
  font-weight: 500;
  display: inline-flex;
  align-items: center;
  transition: color 0.2s ease;
}

.resource-nav a:hover {
  color: #1d4ed8;
}

.arrow {
  margin-left: 0.5rem;
  font-size: 1.1em;
}

.btn-text {
  display: inline-block;
}
</style>