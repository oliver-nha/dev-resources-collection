// App.vue
<script setup>
import { reactive } from "vue";
import StoredResource from "./components/developer-resources/StoredResource.vue";
import TheHeader from "./components/layouts/TheHeader.vue";

const storedResource = reactive([
  {
    id: 'official-guide',
    title: 'Official Guide',
    description: 'The official Vue 3 Guide',
    link: 'https://vuejs.org/guide'
  },
  {
    id: 'react-guide',
    title: 'React Guide',
    description: 'The official React Guide',
    link: 'https://reactjs.org/docs/getting-started.html'
  }
]);
</script>

<template>
  <div class="app">
    <TheHeader title="Dev Resources" />
    <main>
      <StoredResource :resources="storedResource" />
    </main>
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