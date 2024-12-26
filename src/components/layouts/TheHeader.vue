<script setup>
defineProps(['title']);
</script>

<template>
  <header class="main-header">
    <div class="header-content">
      <h1>{{ title }}</h1>
    </div>
  </header>
</template>

<style scoped>
.main-header {
  background: linear-gradient(135deg, #3b82f6 0%, #1d4ed8 100%);
  padding: 1.5rem 0;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.header-content {
  max-width: 48rem;
  margin: 0 auto;
  padding: 0 1rem;
}

h1 {
  color: white;
  margin: 0;
  font-size: 2rem;
  font-weight: 600;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}
</style>