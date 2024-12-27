<script setup>
defineProps(['mode']);
</script>

<template>
   <button :class="mode">
     <slot />
   </button>
</template>

<style scoped>
button {
  padding: 0.625rem 1.25rem;
  font-family: inherit;
  font-weight: 500;
  font-size: 0.875rem;
  background-color: #6366f1;
  border: 1px solid transparent;
  color: white;
  cursor: pointer;
  border-radius: 0.5rem;
  transition: all 0.15s ease;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  line-height: 1.25rem;
}

button:hover {
  background-color: #4f46e5;
  transform: translateY(-1px);
}

button:active {
  transform: translateY(0);
}

.flat {
  background-color: transparent;
  color: #6366f1;
  border: none;
}

.flat:hover {
  background-color: #eef2ff;
}
</style>