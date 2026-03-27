<script setup>
import Button from '../atoms/Button.vue';
import Icon from '../atoms/Icon.vue';

const props = defineProps({
  icon: String,
  label: String,
  selected: Boolean
});

const emit = defineEmits(['select']);
</script>

<template>
  <Button class="transport-option" :class="{ 'transport-option--active': selected }" @click="emit('select')">
    <div class="transport-option__content">
      <Icon :name="icon" />
      <span class="transport-option__label">
        {{ label }}
      </span>
    </div>
  </Button>
</template>

<style scoped>
.transport-option {
  background-color: var(--color-white);
  border: 1px solid var(--color-gray-light);
  padding: 8px;
  width: 70px;
  height: 80px;
  cursor: pointer;
  transition: all 0.2s ease;
}

.transport-option__content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 6px;
}

.transport-option .icon {
  color: var(--color-gray-light);
  transition: color 0.2s ease;
}

.transport-option__label {
  font-size: 10px;
  text-align: center;
  color: var(--color-gray-light);
  transition: color 0.2s ease;
}

.transport-option:hover:not(.transport-option--active) {
  background-color: #f8f9fa;
  border-color: var(--color-gray-dark);
}

.transport-option:hover:not(.transport-option--active) .icon {
  color: var(--color-gray-dark);
}

.transport-option:hover:not(.transport-option--active) .transport-option__label {
  color: black;
}

.transport-option--active {
  background-color: #e6f7ef;
  border: 2px solid var(--color-primary);
  color: var(--color-primary);
  cursor: default;
}

.transport-option--active .icon {
  color: var(--color-primary);
}

.transport-option--active .transport-option__label {
  color: var(--color-primary);
}
</style>