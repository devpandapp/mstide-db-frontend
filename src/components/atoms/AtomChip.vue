<script setup lang="ts">
// Props
const props = defineProps<{
  color?: string;
  size?: string;
  label?: boolean;
}>();
</script>

<template>
  <v-chip :color="props.color" :size="props.size" :label="props.label">
    <slot />
  </v-chip>
</template>
