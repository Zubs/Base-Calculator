<template>
  <div class="home">
    <Converter msg="Welcome to Your Vue.js App 2" />
  </div>
</template>

<script>
// @ is an alias to /src
import Converter from "@/components/Converter.vue";

export default {
  name: "Home",
  components: {
    Converter,
  },
};
</script>
