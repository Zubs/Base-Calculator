<template>
  <v-app>
    <v-container class="my-5">
      <v-form ref="form" class="my-5 text-center">
        <v-text-field solo label="Number" clearable :hint="hint" append-icon="mdi-number" class="my-5">
          <template v-slot:append-outer style="background: red;">
            <v-select solo label="Base" :items="bases"></v-select>
          </template>
        </v-text-field>
        <v-btn x-large depressed fab plain>
          <v-icon x-large color="success">mdi-transfer-down</v-icon>
        </v-btn>
        <v-text-field solo label="Number" clearable :hint="hint" append-icon="mdi-number" class="my-5">
          <template v-slot:append-outer style="background: red;">
            <v-select solo label="Base" :items="bases"></v-select>
          </template>
        </v-text-field>
        <v-btn block color="success">Test</v-btn>
      </v-form>
      <v-card class="pa-5">
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
      }
    }
  }
</script>