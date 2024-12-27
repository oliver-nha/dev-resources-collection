<script setup>
defineProps({
  title:{
    type: String,
    required: false
  }
})

defineEmits(['close'])

</script>

<template>
  <div class="modal-backdrop" @click="$emit('close')"></div>
<dialog open>
  <header>
    <slot name="header">
      <h2>{{ title }}</h2>
    </slot>
  </header>
  <section>
    <slot></slot>
  </section>
  <menu>
    <slot name="actions">
      <base-button @click="$emit('close')">Close</base-button>
    </slot>
  </menu>
</dialog>
</template>

<style scoped>
.modal-backdrop {
  position: fixed;
  top: 0;
  left: 0;
  height: 100vh;
  width: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  backdrop-filter: blur(4px);
  z-index: 50;
  animation: fadeIn 0.2s ease-out;
}

dialog {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 90%;
  max-width: 32rem;
  z-index: 100;
  border-radius: 1rem;
  border: 1px solid rgb(243, 244, 246);
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1),
  0 10px 10px -5px rgba(0, 0, 0, 0.04);
  padding: 0;
  margin: 0;
  background: white;
  animation: slideIn 0.3s ease-out;
}

header {
  background-color: #6366f1;
  color: white;
  padding: 1.25rem 1.5rem;
  border-top-left-radius: 1rem;
  border-top-right-radius: 1rem;
}

header h2 {
  margin: 0;
  font-size: 1.25rem;
  font-weight: 600;
  line-height: 1.5;
}

section {
  padding: 1.5rem;
  max-height: calc(100vh - 16rem);
  overflow-y: auto;
}

menu {
  padding: 1.25rem 1.5rem;
  display: flex;
  justify-content: flex-end;
  gap: 0.75rem;
  border-top: 1px solid rgb(243, 244, 246);
  margin: 0;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translate(-50%, -48%);
  }
  to {
    opacity: 1;
    transform: translate(-50%, -50%);
  }
}

@media (max-width: 640px) {
  dialog {
    width: 95%;
  }
}
</style>