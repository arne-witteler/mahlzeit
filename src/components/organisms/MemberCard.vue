<script setup>
import MemberHeader from '../molecules/MemberHeader.vue';
import TransportOption from '../molecules/TransportOption.vue';

const props = defineProps({
  id: Number,
  name: String,
  avatar: String,
  transport: String
});

const emit = defineEmits(['delete', 'update-transport']);
</script>

<template>
  <li class="member-card">
    <MemberHeader :name="name" :avatar="avatar" @delete="emit('delete', id)" />
    <div class="member-card__transportation">
      <TransportOption icon="walking" label="Zu Fuß" :selected="transport === 'walking'"
        @select="emit('update-transport', 'walking')" />

      <TransportOption icon="transit" label="ÖPNV" :selected="transport === 'transit'"
        @select="emit('update-transport', 'transit')" />

      <TransportOption icon="cycling" label="Fahrrad" :selected="transport === 'cycling'"
        @select="emit('update-transport', 'cycling')" />

      <TransportOption icon="driving" label="Auto" :selected="transport === 'driving'"
        @select="emit('update-transport', 'driving')" />
    </div>
  </li>
</template>

<style scoped>
.member-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 16px;
  padding: 12px;
  border: 1px solid #e0e0e0;
  border-radius: 8px;
}

.member-card__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 12px;
  width: 100%;
}

.member-card__info {
  display: flex;
  justify-content: flex-start;
  align-items: top;
  gap: 12px;
  width: 100%;
}

.member-card__avatar {
  flex-shrink: 0;
  background-color: var(--color-primary);
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  width: 30px;
  height: 30px;
}

.member-card__info {
  flex: 1;
}

.member-card__transportation {
  display: flex;
  gap: 8px;
}

.member-card__transportation-button {
  flex-shrink: 0;
  font-size: 10px;
  border: 1px solid black;
  color: black;
  background-color: var(--color-white);
  display: flex;
  flex-direction: column;
}
</style>