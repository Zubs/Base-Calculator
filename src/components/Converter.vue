<template>
  <v-app>
    <v-container class="my-5">
      <v-form ref="form" class="my-5 text-center">
        <v-text-field
          solo
          label="Number To Convert"
          clearable
          :hint="hint"
          append-icon="mdi-number"
          class="my-5"
          :rules="rules"
          v-model="input"
        ></v-text-field>
        <v-row>
          <v-col cols="6">
            <v-select
              solo
              :items="bases"
              label="Base From"
              :rules="baseRules"
              @change="setRules()"
              v-model="baseFrom"
            ></v-select>
          </v-col>
          <v-col cols="6">
            <v-select
              solo
              :items="bases"
              label="Base To"
              :rules="baseRules"
              v-model="baseTo"
            ></v-select>
          </v-col>
        </v-row>
        <v-btn block color="success" @click="convert">Convert</v-btn>
      </v-form>
      <v-card class="pa-5" v-if="result">
        <v-card-text>
          <h1>
            {{ result }}
            <v-icon @click="copyResult()">mdi-content-copy</v-icon>
          </h1>
        </v-card-text>
      </v-card>
    </v-container>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      input: "",
      baseFrom: null,
      baseTo: null,
      bases: ["Binary (2)", "Octal (8)", "Decimal (10)", "Hexadecimal (16)"],
      baseValues: {
        "Binary (2)": 2,
        "Octal (8)": 8,
        "Decimal (10)": 10,
        "Hexadecimal (16)": 16,
      },
      hint: "Number to convert",
      rules: [(v) => !!v || "Enter Number To Convert"],
      baseRules: [(v) => !!v || "Choose A Base"],
      result: 0,
    };
  },

  methods: {
    convert() {
      // Remove previous result
      this.result = null;

      // Validate inputs
      if (this.$refs.form.validate()) {
        if (this.baseFrom === this.baseTo) {
          this.result = this.input;
        } else {
          this.result = parseInt(
            this.input,
            this.baseValues[this.baseFrom]
          ).toString(this.baseValues[this.baseTo]);
        }
      }
    },

    setRules() {
      if (this.baseFrom === this.bases[0]) {
        // Set Base 2 Rule
        this.rules[1] = (v) => /[0-1]/.test(v) || "Number Must Be Less Than 2";
      } else if (this.baseFrom === this.bases[1]) {
        // Set Base 8 Rule
        this.rules[1] = (v) => /[0-7]/.test(v) || "Number Must Be Less Than 8";
      } else if (this.baseFrom === this.bases[2]) {
        // Set Base 10 Rule
        this.rules[1] = (v) =>
          /[0-9]/.test(v) || "Only numeric characters are allowed";
      } else if (this.baseFrom === this.bases[3]) {
        // Set Base 16 Rule
        this.rules[1] = (v) =>
          /[0-9A-Fa-f]/.test(v) || "Number Must Be Less Than 16";
      }
    },

    async copyResult() {
      // Copy result to clipboard
      await navigator.clipboard.writeText(this.result);
    },
  },
};
</script>
