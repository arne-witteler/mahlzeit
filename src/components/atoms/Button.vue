<script setup>
import Icon from './Icon.vue';

const props = defineProps({
  icon: String,
  title: String
});

const emit = defineEmits(['click']);
</script>

<template>
  <button class="button" @click="emit('click')">

    <slot>
      <Icon v-if="icon" :name="icon" />
      <span v-if="title">{{ title }}</span>
    </slot>

  </button>
</template>

<style scoped>
.button {
  padding: 8px 16px;
  background: var(--color-primary);
  color: var(--color-white);
  border: none;
  border-radius: 8px;
  cursor: pointer;
}
</style>