// App.vue
<script setup>


import TheHeader from "./components/layouts/TheHeader.vue";
import TheResources from "@/components/developer-resources/TheResources.vue";

</script>

<template>
  <div class="app">
    <TheHeader title="Dev Resources" />
    <TheResources />
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

:root {
  --background-color: #f3f4f6;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html {
  font-family: 'Inter', sans-serif;
  background-color: var(--background-color);
}

body {
  margin: 0;
  line-height: 1.5;
  color: #111827;
}

main {
  padding: 2rem 0;
}

.app {
  min-height: 100vh;
}
</style>