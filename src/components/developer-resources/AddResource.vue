<script setup>
import BaseCard from "../UI/BaseCard.vue";
import BaseButton from "../UI/BaseButton.vue";
</script>

<template>
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
              required
          >
        </div>

        <div class="form-group">
          <label for="description">Description</label>
          <textarea
              id="description"
              name="description"
              rows="3"
              class="form-input"
              required
          ></textarea>
        </div>

        <div class="form-group">
          <label for="link">Link</label>
          <input
              type="url"
              id="link"
              name="link"
              class="form-input"
              required
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