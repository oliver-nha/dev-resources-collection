<script setup>
import TheHeader from "./components/layouts/TheHeader.vue";
import TheResources from "@/components/developer-resources/TheResources.vue";
</script>

<template>
  <div class="app">
    <TheHeader title="Learning Resources" />
    <TheResources />
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap');

:root {
  --primary-color: #6366f1;
  --primary-dark: #4f46e5;
  --background-color: #f8fafc;
  --text-primary: #1e293b;
  --text-secondary: #64748b;
  --card-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html {
  font-family: 'Poppins', sans-serif;
  background-color: var(--background-color);
}

body {
  color: var(--text-primary);
  line-height: 1.6;
}

.app {
  min-height: 100vh;
}
</style>