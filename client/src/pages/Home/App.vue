<template>
  <div>
    <Header />
    <Body />
  </div>
</template>

<script>
const axios = require("axios");
import Header from "./components/Header.vue";
import Body from "./components/Body.vue";

export default {
  components: { Header, Body },
  data () { 
    return {
      results: [[[]]],
    };
  },
  methods: {
    uporabniki() {
      axios.post("http://localhost:3000/api/uporabniki").then((response) => {
        this.results = response.data;
      });
    }
  },
  mounted() {
    this.uporabniki();
  }
}
</script>

<style>
#app {
  margin: 0 auto;
  font-weight: normal;
  font-family: latoregular, Lato, sans-serif;
}
</style>
