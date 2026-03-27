<script setup>
import Icon from '../atoms/Icon.vue';
import MemberCard from './MemberCard.vue';
import Button from '../atoms/Button.vue';
import { ref } from 'vue';

const members = ref([
  {
    id: 1,
    name: 'Alice Johnson',
    homeAddress: 'Prinzessinnenstraße 1, 10969 Berlin',
    officeAddress: 'Prinzessinnenstraße 1, 10969 Berlin',
    transport: 'walking'
  },
  {
    id: 2,
    name: 'Bob Smith',
    homeAddress: 'Prinzessinnenstraße 1, 10969 Berlin',
    officeAddress: 'Prinzessinnenstraße 1, 10969 Berlin',
    transport: 'transit',
    avatar: '/src/images / person - icon.png'
  },
  {
    id: 3,
    name: 'Charlie Davis',
    homeAddress: 'Prinzessinnenstraße 1, 10969 Berlin',
    officeAddress: 'Prinzessinnenstraße 1, 10969 Berlin',
    transport: 'cycling',
    avatar: '/src/images / person - icon.png'
  },
]);

function addMember() {
  members.value.push({
    id: Date.now(),
    name: 'New Member',
    homeAddress: 'Prinzessinnenstraße 1, 10969 Berlin',
    officeAddress: 'Prinzessinnenstraße 1, 10969 Berlin',
    transport: 'walking'
  });
}

function removeMember(id) {
  members.value = members.value.filter(member => member.id !== id);
}

function updateTransport(id, transport) {
  const member = members.value.find(m => m.id === id);
  if (member) {
    member.transport = transport;
  }
}

function updateHomeAddress(id, value) {
  const member = members.value.find(m => m.id === id);
  if (member) member.homeAddress = value;
}

function updateOfficeAddress(id, value) {
  const member = members.value.find(m => m.id === id);
  if (member) member.officeAddress = value;
}

</script>

<template>
  <aside class="sidebar">
    <header class="sidebar__header">
      <div class="sidebar__branding">
        <div class="sidebar__logo">
          <Icon name="logo" />
        </div>
        <div class="sidebar__title-group">
          <h1 class="sidebar__title">Mahlzeit</h1>
          <p class="sidebar__subtitle">Find the perfect spot for your team lunch</p>
        </div>
      </div>
    </header>

    <div class="sidebar__content">
      <div class="sidebar__section-header">
        <h3>Team Members ({{ members.length }})</h3>
        <Button icon="add" title="Add" @click="addMember" />
      </div>

      <ul class="member-card-list">
        <MemberCard v-for="member in members" :key="member.id" :id="member.id" :name="member.name"
          :avatar="member.avatar" :transport="member.transport" :homeAddress="member.homeAddress"
          :officeAddress="member.officeAddress" @delete="removeMember"
          @update-transport="(value) => updateTransport(member.id, value)"
          @update:homeAddress="val => updateHomeAddress(member.id, val)"
          @update:officeAddress="val => updateOfficeAddress(member.id, val)" />
      </ul>
    </div>

    <div class="sidebar__footer">
      <div class="sidebar__footer-button-wrapper">
        <Button class="sidebar__footer-button" title="Find best Option"></Button>
      </div>
    </div>
  </aside>
</template>

<style scoped>
.member-card-list {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

.sidebar {
  display: flex;
  flex-direction: column;
  height: 100vh;
  width: 400px;
  background-color: var(--color-white);
  border-right: 1px solid #e0e0e0;
}

.sidebar__header {
  background: linear-gradient(var(--color-primary), var(--color-secondary));
  padding: 24px 20px;
  color: var(--color-white);
}

.sidebar__branding {
  display: flex;
  align-items: center;
  gap: 12px;
}

.sidebar__logo {
  background: var(--color-white);
  padding: 8px;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.sidebar__title {
  font-size: 1.5rem;
  font-weight: 700;
  margin: 0;
}

.sidebar__subtitle {
  font-size: 0.85rem;
  margin: 0;
  opacity: 0.9;
}

.sidebar__content {
  flex: 1;
  padding: 20px;
  overflow-y: auto;
}

.sidebar__section-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}

.sidebar__footer {
  padding: 20px;
  border-top: 1px solid #eee;
}

.sidebar__footer-button-wrapper {
  display: flex;
  justify-content: center;
  width: 100%;
}

.sidebar__footer-button {
  width: 100%;
}
</style>