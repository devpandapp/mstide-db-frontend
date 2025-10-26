<script setup lang="ts">
// Core
import { computed } from 'vue';

// Interfaces
import type { MassTable } from '@/interfaces/MassTable';

// Props
const props = defineProps<{
  massSpectra: MassTable[][];
}>();

const commonMz = computed(() => {
  if (props.massSpectra.length <= 1) return [];
  return props.massSpectra
    .map((arr) => arr.map((e) => e.mz))
    .reduce((a, b) => a.filter((mz) => b.includes(mz)));
});
</script>

<template>
  <v-data-table v-if="massSpectra.length > 1" class="elevation-1" hide-default-footer hide-no-data>
    <template v-slot:headers>
      <tr>
        <th class="text-center">
          <strong>Common <i>m/z</i></strong>
        </th>
        <th v-for="(entry, index) in commonMz" :key="'mz-' + index" class="text-center">
          {{ entry }}
        </th>
      </tr>
    </template>
  </v-data-table>

  <v-data-table v-else class="elevation-1" hide-default-footer>
    <template v-slot:headers>
      <tr>
        <th class="text-center border-sm">
          <strong><i>m/z</i></strong>
        </th>
        <th
          v-for="(entry, index) in massSpectra[0]"
          :key="'mz-' + index"
          class="text-center border-sm"
        >
          {{ entry.mz }}
        </th>
      </tr>
    </template>

    <template v-slot:body>
      <tr>
        <td class="text-center border-sm"><strong>Intensity</strong></td>
        <td
          v-for="(entry, index) in massSpectra[0]"
          :key="'intensity-' + index"
          class="text-center border-sm"
        >
          {{ entry.intensity }}
        </td>
      </tr>
    </template>
  </v-data-table>
</template>
