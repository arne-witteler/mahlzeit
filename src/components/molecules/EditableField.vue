<script setup>
import { ref } from 'vue';

const props = defineProps({
  modelValue: String
});

const emit = defineEmits(['update:modelValue']);

const isEditing = ref(false);
const value = ref('');

function startEditing() {
  value.value = props.modelValue || '';
  isEditing.value = true;
}

function stopEditing() {
  isEditing.value = false;
  emit('update:modelValue', value.value);
}
</script>

<template>
  <div class="editable-field" @click="startEditing">

    <template v-if="!isEditing">
      <div class="editable-field__display">
        <Icon name="location" class="editable-field__icon" />
        <span class="editable-field__text">
          {{ props.modelValue || 'Adresse hinzufügen' }}
        </span>
      </div>
    </template>

    <input v-else v-model="value" class="editable-field__input" @blur="stopEditing" @keyup.enter="stopEditing"
      autofocus />

  </div>
</template>

<style scoped>
.editable-field {
  width: 100%;
}

.editable-field__display {
  display: flex;
  align-items: center;
  gap: 8px;

  background-color: #f5f6f7;
  border: 1px solid #e0e0e0;
  border-radius: 10px;

  padding: 10px 12px;
  cursor: pointer;
  transition: all 0.2s ease;
  margin-right: 50px;
}

.editable-field__display:hover {
  border-color: #c5c5c5;
}

.editable-field__icon {
  color: var(--color-gray-light);
}

.editable-field__text {
  font-size: 14px;
  color: #333;
}

.editable-field__input {
  width: 100%;
  padding: 10px 12px;

  border-radius: 10px;
  border: 1px solid var(--color-primary);

  outline: none;
}
</style>