<script setup lang="ts">
// Modules
import { mdiMolecule, mdiAtom } from '@mdi/js';

// Components
import AtomButton from '@/components/atoms/AtomButton.vue';

// Data
const features = [
  {
    title: 'List of compounds',
    desc: 'Browse all nucleotide compounds in the MSTIDE database with their structures, spectra, peak lists, and proposed fragment assignments.',
    link: '/compound/list',
    icon: mdiMolecule,
  },
  {
    title: 'List of fragments',
    desc: 'View identified ion fragments with proposed structures and spectral data for detailed analysis of nucleotide fragmentation.',
    link: '/fragment/list',
    icon: mdiAtom,
  },
];
</script>

<template>
  <v-main>
    <v-container class="pa-sm-6 pa-md-12" fluid>
      <v-responsive class="text-center mx-auto" max-width="700">
        <h1 class="mt-2">MSTIDE Database 2.0</h1>

        <p class="mt-4 text-body-1 text-medium-emphasis">
          The database is a repository of negative ion tandem mass spectrometry data for natural
          nucleotides and their synthetic derivatives. These compounds included numerous
          biologically and pharmaceutically significant dinucleotides, varying in the type of
          nitrogenous base, the length of the oligophosphate chain (from mono- to pentaphosphate),
          and the presence of additional modifications in the phosphate, ribose, or nitrogenous
          baseresidues...
        </p>

        <p class="mt-4">
          <AtomButton color="secondary" href="/about" target="_blank"> Read more </AtomButton>
        </p>

        <p class="mt-5"></p>

        <p class="text-left" v-for="(item, i) in features" :key="i">
          <v-card class="mx-auto" :href="item.link" rel="noopener" target="_blank" variant="text">
            <v-card-title><v-icon :icon="item.icon"></v-icon> {{ item.title }}</v-card-title>
            <v-card-subtitle>Go to page</v-card-subtitle>
            <v-card-text>{{ item.desc }}</v-card-text>
          </v-card>
        </p>
      </v-responsive>
    </v-container>
  </v-main>
</template>
