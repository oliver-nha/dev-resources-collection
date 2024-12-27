<script setup>
defineProps(['title']);
</script>

<template>
  <header class="header">
    <div class="header-content">
      <h1>{{ title }}</h1>
    </div>
  </header>
</template>

<style scoped>
.header {
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--primary-dark) 100%);
  padding: 2rem 0;
  margin-bottom: 2rem;
}

.header-content {
  max-width: 64rem;
  margin: 0 auto;
  padding: 0 1.5rem;
}

h1 {
  color: white;
  font-size: 2.25rem;
  font-weight: 700;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}
</style>