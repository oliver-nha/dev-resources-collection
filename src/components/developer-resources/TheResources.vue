<!--<script setup>-->
<!--import {ref, computed, provide} from 'vue';-->
<!--import StoredResource from './StoredResource.vue';-->
<!--import AddResource from './AddResource.vue';-->
<!--const selectedTab = ref('stored-resource');-->
<!--const storedResources = ref([-->
<!--  {-->
<!--    id: 'vue-official-guide',-->
<!--    title: 'Vue Official Guide',-->
<!--    description: 'The official Vue.js documentation',-->
<!--    link: 'https://vuejs.org',-->
<!--  },-->
<!--  {-->
<!--    id: 'react-official-guide',-->
<!--    title: 'React Official Guide',-->
<!--    description: 'The official React.js documentation',-->
<!--    link: 'https://reactjs.org',-->
<!--  },-->
<!--  {-->
<!--    id: 'svelte-official-guide',-->
<!--    title: 'Svelte Official Guide',-->
<!--    description: 'The official Svelte.js documentation',-->
<!--    link: 'https://svelte.dev/',-->
<!--  },-->
<!--  {-->
<!--    id: 'angular-official-guide',-->
<!--    title: 'Angular Official Guide',-->
<!--    description: 'The official Angular.js documentation',-->
<!--    link: 'https://angular.io/',-->
<!--  },-->
<!--  {-->
<!--    id: 'jquery-official-guide',-->
<!--    title: 'jQuery Official Guide',-->
<!--    description: 'The official jQuery documentation',-->
<!--    link: 'https://jquery.com/',-->
<!--  },-->
<!--]);-->
<!--provide('resources', storedResources);-->
<!--const setSelectedTab = (tab) => {-->
<!--  selectedTab.value = tab;-->
<!--};-->
<!--const tabComponents = {-->
<!--  'stored-resource': StoredResource,-->
<!--  'add-resource': AddResource,-->
<!--};-->
<!--const storedResBtnMode = computed(() =>-->
<!--    selectedTab.value === 'stored-resource' ? 'outline&#45;&#45;selected' : 'outline'-->
<!--);-->

<!--const addResBtnMode = computed(() =>-->
<!--    selectedTab.value === 'add-resource' ? 'outline&#45;&#45;selected' : 'outline'-->
<!--);-->
<!--</script>-->

<!--<template>-->
<!--  <div class="row">-->
<!--    <div class="tabs">-->
<!--      <base-card color="gray">-->
<!--        <base-button-->
<!--            @click="setSelectedTab('stored-resource')"-->
<!--            :mode="storedResBtnMode"-->
<!--        >-->
<!--          Stored resources-->
<!--        </base-button>-->
<!--        <base-button-->
<!--            @click="setSelectedTab('add-resource')"-->
<!--            :mode="addResBtnMode"-->
<!--        >-->
<!--          Add resource-->
<!--        </base-button>-->
<!--      </base-card>-->
<!--    </div>-->
<!--    &lt;!&ndash; Dynamically render the component &ndash;&gt;-->
<!--    <component :is="tabComponents[selectedTab]" />-->
<!--  </div>-->
<!--</template>-->
<script setup>
import AppTabs from "@/components/layouts/AppTabs.vue";
import StoredResource from "@/components/developer-resources/StoredResource.vue";
import AddResource from "@/components/developer-resources/AddResource.vue";
import AppTab from "@/components/layouts/AppTab.vue";
import {computed, provide, ref} from "vue";
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

</script>
<template>
     <AppTabs >
       <AppTab title="stored-resource">
          <StoredResource />
       </AppTab>
      <AppTab title="add-resource">
        <AddResource />
      </AppTab>
     </AppTabs>
</template>