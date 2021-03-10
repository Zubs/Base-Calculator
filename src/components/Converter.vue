<template>
  <v-app>
    <v-container class="my-5">
      <v-form ref="form" class="my-5 text-center">
        <v-text-field solo label="Number" clearable :hint="hint" append-icon="mdi-number" class="my-5" :rules="rules" v-model="input" type="number"></v-text-field>
        <v-row>
          <v-col cols="6">
            <v-select solo :items="bases" label="Base From" :rules="baseRules" @change="setRules()" v-model="baseFrom"></v-select>
          </v-col>
          <v-col cols="6">
            <v-select solo :items="bases" label="Base To" :rules="baseRules" v-model="baseTo"></v-select>
          </v-col>
        </v-row>
        <v-btn block color="success" @click="convert">Convert</v-btn>
      </v-form>
      <v-card class="pa-5" v-if="result">
        <v-card-text>
          <h1>{{ result }}</h1>
        </v-card-text>
      </v-card>
    </v-container>
  </v-app>
</template>

<script>
  export default {
    data () {
      return {
        input: "",
        baseFrom: null,
        baseTo: null,
        bases: [
            "Binary (2)", 
            "Octal (8)",
            "Decimal (10)",
            "Hexadecimal (16)",
        ],
        hint: "This is dynamic",
        rules: [
          v => !!v || 'Enter Number To Convert',
        ],
        baseRules: [
          v => !!v || "Choose A Base",
        ],
        result: 0,
      }
    },

    methods: {
      convert () {
        
        // Validate inputs
        if (this.$refs.form.validate()) {
          
          // Convert Decimal
          if (this.baseFrom == this.bases[2]) {

            // To Binary
            if (this.baseTo == this.bases[0]) {
              this.result = this.decimalToBinary(this.input);
            }
          }
        }
      },

      // The name is descriptive enough
      decimalToBinary (number) {
        return parseInt(number).toString(2); // Found this online
      },

      // Update Rules
      setRules () {
        if (this.baseFrom == this.bases[0]) {

          // Set Base 2 Rule
        } else if (this.baseFrom == this.bases[1]) {

          // Set Base 8 Rule
        } else if (this.baseFrom == this.bases[2]) {

          // Set Base 10 Rule
        } else if (this.baseFrom == this.bases[3]) {

          // Set Base 16 Rule
        }
      },
    }
  }
</script>