<script setup>
import Button from '../atoms/Button.vue';

const props = defineProps({
  name: String,
  avatar: String
});

const emit = defineEmits(['delete']);
</script>

<template>
  <div class="member-header">

    <div class="member-header__info">
      <img :src="avatar" alt="Avatar" />
      <h4 class="member-header__name">{{ name }}</h4>
    </div>

    <Button class="member-header__delete-button" icon="delete" @click="emit('delete')" />

  </div>
</template>

<style scoped>
.member-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}

.member-header__info {
  display: flex;
  align-items: center;
  gap: 12px;
}

.member-header__name {
  font-size: 1rem;
  font-weight: 600;
  margin: 0;
}
</style>