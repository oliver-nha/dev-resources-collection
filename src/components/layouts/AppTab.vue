<script setup >
// Notice that import the injection key from the `AppTabs` component
// since it's a symbol we can be absolutely certain it's unique
// and since these are tightly coupled it makes sense to get it from the parent


// This is a simple title prop
import {computed, inject, readonly, ref} from "vue";

const props = defineProps(['title']);


// This is where the magic happens
// Here we "pick up" the data provided by the parent
// we also give some defaults with the same types as the provided
// to make TypeScript happy and keep our IDE autocompleting things correctly
const tabsProvider = inject('AppTabs', {
  withinTabs: false,
  registerTab: (title) => { },
  activeTab: readonly(ref()),
  activateTab: (title) => { },
});


if (!tabsProvider.withinTabs) {
  throw new Error("AppTab must be used within a AppTabs component");
}

// Here we push our panels title to the parent so that it can display the tabs properly
tabsProvider.registerTab(props.title);

// If there is no active tab set, go ahead and set it
// This will only ever be true for the first panel
// Meaning, the first panel will always be the default active one
if (!tabsProvider.activeTab.value) {
  tabsProvider.activateTab(props.title);
}

// Finally just check to see if this panel should be active
// based on the active `activeTab` state from the parent
const isActive = computed(() => tabsProvider.activeTab.value === props.title);
</script>

<!--- For the display, only show the panel content if it's active -->
<template>
  <div v-show="isActive">
    <slot></slot>
  </div>
</template>