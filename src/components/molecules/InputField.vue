<script setup>
const props = defineProps({
  label: String
});
</script>

<template>
  <div class="input-field">
    <label for="input" class="input-field__label">{{ props.label }}</label>
    <input id="input" type="text" class="input-field__input" placeholder="Enter text here..." />
  </div>
</template>