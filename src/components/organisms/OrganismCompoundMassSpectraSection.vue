<script setup lang="ts">
// Components
import MoleculeMassSpectraTable from '@/components/molecules/MoleculeMassSpectraTable.vue';
import MoleculeMassSpectraChart from '@/components/molecules/MoleculeMassSpectraChart.vue';

// Intrefaces
import type { MassTable } from '@/interfaces/MassTable';

// Props
const props = defineProps<{
  massSpectra: MassTable[][];
}>();
</script>

<template>
  <MoleculeMassSpectraTable :massSpectra="props.massSpectra" />
  <MoleculeMassSpectraChart :massSpectra="props.massSpectra" />
</template>
