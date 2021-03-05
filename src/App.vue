<template>
  <v-app>
    <v-app-bar app color="success" dark>
      <v-toolbar-title><span style='font-family: "Brush Script MT", cursive;'>Base</span><span class="red--text font-weight-bold">Converter</span></v-toolbar-title>
    </v-app-bar>

    <v-main>
      <Converter/>
    </v-main>
  </v-app>
</template>

<script>
import Converter from './components/Converter';

export default {
  name: 'App',

  components: {
    Converter,
  },

  data: () => ({
    //
  }),
};
</script>
