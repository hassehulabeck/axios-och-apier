<template>
  <div id="app">
    <rate-list :ratedata="ratedata" />
  </div>
</template>

<script>
import axios from "axios";
import RateList from "./components/RateList.vue";

export default {
  name: "App",
  data() {
    return {
      url: "https://api.exchangerddatesapi.io/latest?base=SEK",
      ratedata: {
        rates: null,
        baseRate: null,
        date: null,
        error: null,
      },
    };
  },
  components: {
    RateList,
  },
  mounted() {
    axios
      .get(this.url)
      .then((response) => {
        this.ratedata.rates = response.data.rates;
        this.ratedata.baseRate = response.data.base;
        this.ratedata.date = response.data.date;
      })
      .catch((error) => {
        console.error("Fel: " + error);
        this.ratedata.error = "Ojdå, tokigt.";
      });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
