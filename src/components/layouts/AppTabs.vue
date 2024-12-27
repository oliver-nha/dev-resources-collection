<script setup>

// Here we provide a single spot to register all the tabs that should display
// This way we can loop over them and display the clickable tab for each
// It's empty at first because we're letting the child `AppTab`s
// determine the tab titles (based on their "title" prop)
import {computed, provide, readonly, ref} from "vue";
import BaseButton from "@/components/UI/BaseButton.vue";

const tabs = ref([]);

// This is the state that keeps up with the single active tab
// Only one should ever be open at a time
// We'll determine which should be open by
// setting the title of the active tab here
const activeTab = ref();

// This is a helper function for setting the active tab.
// It's important to wrap it in a function if we want to
// allow the child `AppTab` to set an active tab
// Why? Because it's recommended in the Vue docs
// to keep direct mutations of your provided state
// to the component that state is defined in (the parent).
// If you want to allow a child to mutate you should provide a function.
// This keeps the control of the state with the parent
// only allowing the child to mutate the state in the allowed way
function activateTab(title) {
  activeTab.value = title;
}

// This function will allow the child `AppTabs` to register their title
// with the parent `AppTabs`
// Again it's a function because of the reasoning above.
function registerTab(title) {
  if (tabs.value.includes(title)) return;
  tabs.value.push(title);
}

provide('AppTabs', {

  withinTabs: true,

  registerTab,
  activateTab,

  // We expose the active tab to the child
  // but notice we use readonly to keep the child from directly mutating it
  activeTab: readonly(activeTab),
});
const getTab = (tab) => computed(() => (activeTab.value === tab ? null : "flat"));
</script>

<template>
  <div class="tabs">
    <div class="tabs tabs-bordered">
      <base-button v-for="tab in tabs" :key="tab" class="tab" :mode="getTab(tab)"  @click="activateTab(tab)">
        {{ tab }}
      </base-button>
    </div>
    <slot></slot>
  </div>
</template>