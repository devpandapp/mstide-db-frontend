<script setup lang="ts">
// Modules
import { mdiWidgetsOutline, mdiCalendarOutline, mdiCogs } from '@mdi/js';

const features = [
  {
    title: 'Title 1',
    subtitle:
      'Sit quis amet rutrum tellus ullamcorper ultricies libero dolor eget. Sem sodales gravida quam turpis enim lacus amet.',
    icon: mdiWidgetsOutline,
  },
  {
    title: 'Title 2',
    subtitle:
      'QuiArcu egestas dolor vel iaculis in ipsum mauris. Tincidunt mattis aliquet hac quis. Id hac maecenas ac donec pharetra eget.',
    icon: mdiCalendarOutline,
  },
  {
    title: 'Title 3',
    subtitle:
      'QuiArcu egestas dolor vel iaculis in ipsum mauris. Tincidunt mattis aliquet hac quis. Id hac maecenas ac donec pharetra eget.',
    icon: mdiCogs,
  },
];
</script>

<template>
  <v-main>
    <v-container class="pa-6 pa-md-12" fluid>
      <h2 class="font-weight-bold">About MSTIDE Database 2.0</h2>

      <p class="mt-4 mb-6 text-body-1">
        The MSTIDE database is a repository of negative-ion mode tandem mass spectrometry data of
        natural nucleotides and their synthetic derivatives. The compounds include nucleoside mono-,
        di- and tri- phosphates, nucleotide sugars, nucleoside phosphosulfates and their
        counterparts bearing modifications within the (oligo)phosphate, ribose or nucleobase. A
        significant group of compounds featured in the database is nucleotides modified within the
        phosphate with phosphorothioate, phosphoroselenoate, phosphoroamidate, boranophosphate,
        fluorophosphate, methylenebisphosphonate or imidodiphosphate moieties.
      </p>

      <v-row justify="center">
        <v-col cols="12" lg="6" order="2" order-lg="1">
          <p class="text-medium-emphasis mb-5">
            The database was created to accompany a research paper on the fragmentation pathways of
            modified nucleotides: Strzelecka D, Chmielinski S, Bednarek S, Jemielity J, Kowalska J*
            Analysis of mononucleotides by tandem mass spectrometry: investigation of fragmentation
            pathways for phosphate- and ribose-modified nucleotide analogues, Scientific Reports,
            vol. 7, no. 1, Aug. 2017 *Contact corresponding author: Joanna.Kowalska AT fuw.edu.pl
          </p>

          <v-list-item v-for="(item, i) in features" :key="i" class="px-0">
            <template #title>
              <p class="text-body-2 font-weight-bold pb-2">
                <v-icon class="mr-2" color="primary" :icon="item.icon" size="small" />

                {{ item.title }}
              </p>
            </template>

            <template #subtitle>
              <p class="ps-7">{{ item.subtitle }}</p>
            </template>
          </v-list-item>

          <p class="text-medium-emphasis mt-6">
            Information deposited in the database can be browsed via several search options,
            including monoisotopic mass search, peak (m/z) search, multiple peaks search,
            substructure and structural similarity search, filtering of structures by
            modification(s) present in the precursor.
          </p>

          <p class="mt-6 text-h6 font-weight-bold">Simply to learn</p>

          <p class="text-medium-emphasis mt-3">
            In the crucible of stellar nurseries, where hydrogen atoms fuse in the fiery embrace of
            nuclear fusion, the alchemy of creation unfolds, giving birth to new stars and planets
            in a cosmic symphony of birth and destruction. Here, the forces of nature converge in a
            cosmic ballet of elemental forces, shaping the fabric of the universe with their
            intricate interplay.
          </p>
        </v-col>

        <v-col cols="12" lg="5" offset-lg="1" order-lg="2">
          <v-card class="px-6 py-4" elevation="5" rounded="lg" variant="elevated">
            <p class="text-subtitle-1 text-medium-emphasis mt-4 mb-6">
              “Excepteur veniam labore ullamco eiusmod. Pariatur consequat proident duis dolore
              nulla veniam reprehenderit nisi officia voluptate incididunt exercitation exercitation
              elit. Nostrud veniam sint dolor nisi ullamco.”
            </p>

            <v-list-item class="px-0" prepend-avatar="" subtitle="Position" title="Name Surname" />
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>
