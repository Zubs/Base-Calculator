<template>
  <v-app>
    <v-container class="my-5">
      <v-form ref="form" class="my-5 text-center">
        <v-text-field solo label="Number" clearable :hint="hint" append-icon="mdi-number" class="my-5" :rules="rules"></v-text-field>
        <v-row>
          <v-col cols="6">
            <v-select solo :items="bases" label="Base From"></v-select>
          </v-col>
          <v-col cols="6">
            <v-select solo :items="bases" label="Base To"></v-select>
          </v-col>
        </v-row>
        <v-btn block color="success">Convert</v-btn>
      </v-form>
      <v-card class="pa-5" v-if="result">
        <v-card-text>
          <h1>Testing</h1>
        </v-card-text>
      </v-card>
    </v-container>
  </v-app>
</template>

<script>
  export default {
    data () {
      return {
        bases: [
            "Binary (2)", 
            "Octal (8)",
            "Decimal (10)",
            "Hexadecimal (16)",
        ],
        hint: "This is dynamic",
        rules: [],
        result: 0,
      }
    }
  }
</script>