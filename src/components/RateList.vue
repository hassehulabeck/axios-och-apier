<template>
  <div>
    <h1 v-if="ratedata.error">{{ ratedata.error }}</h1>
    <h1 v-else>{{ ratedata.baseRate }}</h1>
    <p>{{ ratedata.date }}</p>
    <ul>
      <li v-for="(value, name) in ratedata.rates" :key="name">
        {{ name }} : {{ value }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "RateList",
  props: {
    ratedata: Object,
  },
};
</script>

<style></style>
