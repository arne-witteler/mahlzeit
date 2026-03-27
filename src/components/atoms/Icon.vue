<script setup lang="ts">
import { computed } from 'vue';

import logoIcon from '@/images/hamburger.svg?component';
import homeIcon from '@/images/house.svg?component';
import officeIcon from '@/images/briefcase-business.svg?component';
import trashIcon from '@/images/trash.svg?component';
import walkIcon from '@/images/footprints.svg?component';
import cycleIcon from '@/images/bike.svg?component';
import transitIcon from '@/images/bus-front.svg?component';
import driveIcon from '@/images/car-front.svg?component';
import plusIcon from '@/images/plus.svg?component';

const iconMap = {
  logo: logoIcon,
  home: homeIcon,
  office: officeIcon,
  delete: trashIcon,
  walking: walkIcon,
  cycling: cycleIcon,
  transit: transitIcon,
  driving: driveIcon,
  add: plusIcon
};

type IconName = keyof typeof iconMap;

const props = defineProps<{
  name: IconName;
}>();

const iconComponent = computed(() => iconMap[props.name]);
</script>

<template>
  <span class="icon" :aria-label="props.name">
    <component :is="iconComponent" />
  </span>
</template>

<style scoped>
.icon {
  width: 20px;
  height: 20px;
}

.icon :deep(svg) {
  fill: none;
  stroke: currentColor;
}
</style>