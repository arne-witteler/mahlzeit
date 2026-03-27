<script setup>
import Icon from '../atoms/Icon.vue';

const props = defineProps({
  label: String,
  icon: String
});
</script>

<template>
  <div class="input-field">

    <div class="input-field__header">
      <Icon v-if="icon" :name="icon" />
      <span class="input-field__label">{{ label }}</span>
    </div>

    <div class="input-field__content">
      <slot />
    </div>

  </div>
</template>

<style scoped>
.input-field {
  display: flex;
  flex-direction: column;
  gap: 8px;
  width: 100%;
}

.input-field__header {
  display: flex;
  align-items: center;
  gap: 10px;
}

.input-field__label {
  font-size: 12px;
  font-weight: 500;
  color: var(--color-gray-dark);
  align-self: flex-end;
}

.input-field__content {
  display: flex;
  gap: 8px;
}
</style>