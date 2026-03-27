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
  <div class="editable-field">
    <span v-if="!isEditing" @click="startEditing">
      {{ props.modelValue || 'Adresse hinzufügen' }}
    </span>
    <input v-else v-model="value" @blur="stopEditing" @keyup.enter="stopEditing" autofocus />

  </div>
</template>