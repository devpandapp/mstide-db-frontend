<template>
  <v-main>
    <v-container class="pa-6 pa-md-12" fluid>
      <h2 class="font-weight-bold">About MSTIDE Database 2.0</h2>

      <p class="mt-4 mb-6 text-body-1">
        The MSTIDE Database 2.0 is an extension of a previously developed resource from our
        laboratory, which contains data on more than 150 mononucleotides (<a
          href="https://www.mstide-db2.com"
          target="_blank"
          >mstide-db2.com</a
        >). It serves as a repository of negative-ion mode tandem mass spectrometry data for di- and
        trinucleotides, encompassing variations in nucleobase composition, oligophosphate chain
        length (from mono- to pentaphosphate), and additional modifications on the phosphate,
        ribose, or nucleobase moieties.
      </p>

      <v-row justify="center">
        <v-col cols="12" lg="6" order="2" order-lg="1">
          <p class="mb-2">
            This database was established to complement a research paper focused on the
            fragmentation mechanisms of modified nucleotides:
          </p>
          <p class="mb-2">
            <b>Zhilyaev D, Strzelecka D, Golojuch S, Pandiurin A, Jemielity J, Kowalska J*</b>
            Analysis of biologically and therapeutically relevant di- and trinucleotide analogues by
            tandem mass spectrometry.
          </p>

          <p class="mb-2">
            <i
              >*Contact corresponding author: Joanna.Kowalska AT
              <a href="https://www.fuw.edu.pl/" target="_blank">fuw.edu.pl</a></i
            >
          </p>

          <p class="text-medium-emphasis mt-6">
            The database covers more than 60 nucleotide compounds, each accompanied by corresponding
            doubly charged MS/MS spectra. For every entry, users can access the parent ion’s
            chemical structure, IUPAC name and abbreviation, detailed measurement conditions, the
            recorded MS/MS spectrum, a numerical list of detected peaks with normalized intensities,
            and a set of proposed chemical structures for identified fragment ions. All fragments
            were manually assigned and evaluated by the authors of the referenced study. MS/MS
            spectra were obtained using carefully optimized collision energies and depolarization
            potentials to ensure comprehensive fragmentation data for each compound. Throughout the
            study, soft ionization was performed using electrospray ionization (ESI), and
            fragmentation was achieved through collision-induced dissociation (CID). Only peaks with
            intensities above 1% of the base peak were included in the final spectra extracted from
            the original raw data.
          </p>

          <p class="text-medium-emphasis mt-4">
            The database provides multiple search functionalities, including monoisotopic mass
            search, single or multiple m/z peak searches, substructure and structural similarity
            searches, as well as filtering of compounds based on modification(s) present in the
            precursor.
          </p>

          <p class="text-medium-emphasis mt-4">
            The database is intended to facilitate detailed analysis of nucleotide fragmentation
            patterns, enabling easier identification of metabolites, synthetic products, fragment
            ions, and nucleotide modifications. The information it contains can support the
            development of mass spectrometry–based methods for diagnosing nucleotide-related
            diseases, identifying nucleotide metabolites, and performing quantitative analyses of
            selected nucleotides. It can also be applied to the rapid, low-material identification
            of nucleotide-derived synthetic products. All data in the library is available free of
            charge, no registration required.
          </p>
        </v-col>

        <v-col cols="12" lg="5" offset-lg="1" order-lg="2">
          <v-card class="px-6 py-4" elevation="5" rounded="lg" variant="elevated">
            <p class="text-subtitle-1 text-medium-emphasis mt-4 mb-6">
              Instructions will be added in the next update.
            </p>

            <!-- <v-list-item class="px-0" prepend-avatar="" subtitle="Position" title="Name Surname" /> -->
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>
