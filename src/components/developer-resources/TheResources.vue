<script setup>
import {ref, computed, provide} from 'vue';
import StoredResource from './StoredResource.vue';
import AddResource from './AddResource.vue';
const selectedTab = ref('stored-resource');
const storedResources = ref([
  {
    id: 'vue-official-guide',
    title: 'Vue Official Guide',
    description: 'The official Vue.js documentation',
    link: 'https://vuejs.org',
  },
  {
    id: 'react-official-guide',
    title: 'React Official Guide',
    description: 'The official React.js documentation',
    link: 'https://reactjs.org',
  },
  {
    id: 'svelte-official-guide',
    title: 'Svelte Official Guide',
    description: 'The official Svelte.js documentation',
    link: 'https://svelte.dev/',
  },
  {
    id: 'angular-official-guide',
    title: 'Angular Official Guide',
    description: 'The official Angular.js documentation',
    link: 'https://angular.io/',
  },
  {
    id: 'jquery-official-guide',
    title: 'jQuery Official Guide',
    description: 'The official jQuery documentation',
    link: 'https://jquery.com/',
  },
]);
provide('resources', storedResources);

const setSelectedTab = (tab) => {
  selectedTab.value = tab;
};
const tabComponents = {
  'stored-resource': StoredResource,
  'add-resource': AddResource,
};
const storedResBtnMode = computed(() =>
    selectedTab.value === 'stored-resource' ? null : 'flat'
);

const addResBtnMode = computed(() =>
    selectedTab.value === 'add-resource' ? null : 'flat'
);
const addResource = (title, description, link) => {
  const newResource = {
    id: new Date().toISOString(),
    title: title,
    description: description,
    link: link,
  };
  storedResources.value.unshift(newResource);
  setSelectedTab('stored-resource');
}
const removeResource = (id) => {
  const resIndex = storedResources.value.findIndex((res) => res.id === id);
  storedResources.value.splice(resIndex, 1);
}
provide('addResource', addResource);
provide('removeResource', removeResource);

</script>

<template>
  <div class="row">
    <div class="tabs">
      <base-card color="gray">
        <!-- events fall through to root element of our custom component -->
        <base-button
            @click="setSelectedTab('stored-resource')"
            :mode="storedResBtnMode"
        >Stored resources</base-button
        >
        <base-button
            @click="setSelectedTab('add-resource')"
            :mode="addResBtnMode"
        >Add resource</base-button
        >
      </base-card>
    </div>
    <!-- component will be cached -->
    <keep-alive>
      <component :is="tabComponents[selectedTab]"></component>
    </keep-alive>
  </div>

</template>
<style scoped>
.tabs {
  margin: 1.5rem 0;
  text-align: center;
}

.row {
  max-width: 800px;
  margin: 0 auto;
  padding: 0 1rem;
}

</style>