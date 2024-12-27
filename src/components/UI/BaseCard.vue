<template>
  <div class="card">
    <slot></slot>
  </div>
</template>

<style scoped>
.card {
  background: white;
  border-radius: 1rem;
  box-shadow: var(--card-shadow);
  padding: 2rem;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.card:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1),
  0 4px 6px -2px rgba(0, 0, 0, 0.05);
}
</style>