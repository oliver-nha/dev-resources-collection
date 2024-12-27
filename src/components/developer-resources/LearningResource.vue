<script setup>
import BaseButton from "../UI/BaseButton.vue";
import BaseCard from "../UI/BaseCard.vue";

defineProps(['id', 'title', 'description', 'link']);
</script>

<template>
  <li class="resource">
    <BaseCard>
      <div class="resource-header">
        <h3>{{ title }}</h3>
        <BaseButton mode="flat">Delete</BaseButton>
      </div>

      <p class="description">{{ description }}</p>

      <div class="resource-actions">
        <a :href="link" target="_blank" rel="noopener noreferrer" class="resource-link">
          View Resource
          <svg xmlns="http://www.w3.org/2000/svg" class="icon" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M10.293 5.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L12.586 11H5a1 1 0 110-2h7.586l-2.293-2.293a1 1 0 010-1.414z" clip-rule="evenodd" />
          </svg>
        </a>
      </div>
    </BaseCard>
  </li>
</template>

<style scoped>
.resource {
  list-style: none;
  margin-bottom: 1.5rem;
}

.resource-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-bottom: 1rem;
  border-bottom: 1px solid #e2e8f0;
}

h3 {
  font-size: 1.25rem;
  font-weight: 600;
  color: var(--text-primary);
}

.description {
  margin: 1rem 0;
  color: var(--text-secondary);
}

.resource-actions {
  margin-top: 1.5rem;
}

.resource-link {
  display: inline-flex;
  align-items: center;
  color: var(--primary-color);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.2s ease;
}

.resource-link:hover {
  color: var(--primary-dark);
}

.icon {
  width: 1.25rem;
  height: 1.25rem;
  margin-left: 0.5rem;
}
</style>