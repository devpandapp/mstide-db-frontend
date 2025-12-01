<script setup lang="ts">
// Core
import { ref, computed, watch } from 'vue';
import { useRoute } from 'vue-router';

// Modules
import { mdiEye, mdiEyeOff } from '@mdi/js';

// Components
import { appState } from '@/db/auth.ts';

// Interfaces
import type { MassTable } from '@/interfaces/MassTable';

// Route
const route = useRoute();

// Data
const localMassSpectra = ref<MassTable[][]>([]);

// Props
const props = defineProps<{
  massSpectra: MassTable[][];
}>();

// Emits
const emit = defineEmits<{
  (e: 'update:massSpectra', value: MassTable[][]): void;
}>();

// Methods
const toggleColumn = (index: number) => {
  const updated = localMassSpectra.value.map((table) =>
    table.map((entry, i) => (i === index ? { ...entry, visible: !entry.visible } : entry))
  );

  emit('update:massSpectra', updated);
};

const normalizeSpectra = (src: MassTable[][]): MassTable[][] => {
  return src.map((table) =>
    table.map((entry) => ({
      ...entry,
      visible: entry.visible ?? true,
    }))
  );
};

// Computed
const commonMz = computed(() => {
  if (props.massSpectra.length <= 1) return [];
  return props.massSpectra
    .map((arr) => arr.map((e) => e.mz))
    .reduce((a, b) => a.filter((mz) => b.includes(mz)));
});

const isAvailableForChange = computed(
  () => (route.name === 'CompoundEdit' || route.name === 'CompoundNew') && appState.isLoggedIn
);

// Watchers
watch(
  () => props.massSpectra,
  (newVal) => {
    localMassSpectra.value = normalizeSpectra(newVal);
  },
  { deep: true }
);

localMassSpectra.value = normalizeSpectra(props.massSpectra);
</script>

<template>
  <v-data-table
    v-if="localMassSpectra.length > 1"
    class="elevation-1"
    hide-default-footer
    hide-no-data
  >
    <template v-slot:headers>
      <tr>
        <th class="text-center border-sm">
          <strong>Common <i>m/z</i></strong>
        </th>
        <th v-for="(entry, index) in commonMz" :key="'mz-' + index" class="text-center border-sm">
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
          v-for="(entry, index) in localMassSpectra[0]"
          :key="'mz-' + index"
          :class="[
            'text-center',
            'border-sm',
            {
              'cursor-pointer': isAvailableForChange,
              'bg-green-lighten-4': entry.visible,
              'bg-red-lighten-4': !entry.visible,
            },
          ]"
          @click="isAvailableForChange ? toggleColumn(index) : null"
        >
          <div class="d-flex flex-column align-center">
            <v-icon :icon="entry.visible ? mdiEye : mdiEyeOff" />
            {{ entry.mz }}
          </div>
        </th>
      </tr>
    </template>

    <template v-slot:body>
      <tr>
        <td class="text-center border-sm"><strong>Intensity</strong></td>
        <td
          v-for="(entry, index) in localMassSpectra[0]"
          :key="'intensity-' + index"
          :class="[
            'text-center',
            'border-sm',
            {
              'cursor-pointer': isAvailableForChange,
              'bg-green-lighten-4': entry.visible,
              'bg-red-lighten-4': !entry.visible,
            },
          ]"
          @click="isAvailableForChange ? toggleColumn(index) : null"
        >
          {{ entry.intensity }}
        </td>
      </tr>
    </template>
  </v-data-table>
</template>
