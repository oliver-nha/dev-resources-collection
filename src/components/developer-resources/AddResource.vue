<script setup>
import BaseCard from "../UI/BaseCard.vue";
import BaseButton from "../UI/BaseButton.vue";
import {inject, onMounted, ref, useTemplateRef} from "vue";
import BaseDialog from "@/components/UI/BaseDialog.vue";
 const addResource = inject('addResource');
const enteredTitle = useTemplateRef('titleInput');
const enteredDescription = useTemplateRef('descriptionInput');
const enteredLink = useTemplateRef('linkInput');
const inputIsInvalid = ref(false);
onMounted(() => {
  enteredTitle.value.focus();
})

const submitForm = () => {
  const enteredTitleValue = enteredTitle.value.value;
  const enteredDescriptionValue = enteredDescription.value.value;
  const enteredLinkValue = enteredLink.value.value;

  if(
      enteredTitleValue.trim() === '' ||
      enteredDescriptionValue.trim() === '' ||
      enteredLinkValue.trim() === ''
  ) {
    inputIsInvalid.value = true;
    return;
  }
  addResource(enteredTitleValue, enteredDescriptionValue, enteredLinkValue);
};
const confirmError = () => {
  inputIsInvalid.value = false
}
</script>

<template>
  <BaseDialog v-if="inputIsInvalid" title="Invalid Input" @close="confirmError">
    <template #default>
      <p>Unfortunately, at least one input value is invalid.</p>
      <p>Please check all inputs and try again.</p>
    </template>
    <template #actions>
      <base-button @click="confirmError" mode="cta">Okay</base-button>
    </template>
  </BaseDialog>
  <div class="add-resource">
    <BaseCard>
      <form @submit.prevent="submitForm" class="form">
        <div class="form-group">
          <label for="title">Title</label>
          <input
              type="text"
              id="title"
              name="title"
              class="form-input"
              ref="titleInput"

          >
        </div>

        <div class="form-group">
          <label for="description">Description</label>
          <textarea
              id="description"
              name="description"
              rows="3"
              class="form-input"
              ref="descriptionInput"

          ></textarea>
        </div>

        <div class="form-group">
          <label for="link">Link</label>
          <input
              type="url"
              id="link"
              name="link"
              class="form-input"
              ref="linkInput"

          >
        </div>

        <div class="form-actions">
          <BaseButton type="submit">Add Resource</BaseButton>
        </div>
      </form>
    </BaseCard>
  </div>
</template>

<style scoped>
.add-resource {
  max-width: 64rem;
  margin: 0 auto;
  padding: 0 1.5rem;
}

.form {
  display: grid;
  gap: 1.5rem;
}

.form-group {
  display: grid;
  gap: 0.5rem;
}

label {
  font-weight: 500;
  color: var(--text-primary);
}

.form-input {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #e2e8f0;
  border-radius: 0.5rem;
  font-family: inherit;
  font-size: 0.875rem;
  transition: all 0.2s ease;
}

.form-input:focus {
  outline: none;
  border-color: var(--primary-color);
  box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.1);
}

.form-actions {
  margin-top: 1rem;
}
</style>