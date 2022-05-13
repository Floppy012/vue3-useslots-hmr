<template>
  <template v-for="(vnode, index) in vnodes" :key="index">
    <component :is="vnode"></component><br>
  </template>
</template>

<script lang="ts" setup>
import { computed, useSlots } from 'vue';
const vnodes = computed(() => {
  console.log("update");
  const defaultSlot = useSlots().default();
  return defaultSlot.filter((vnode) => "data-test" in vnode.props);
});

</script>