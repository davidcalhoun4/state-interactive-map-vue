<template>
  <div class="home">
    <h2 v-for="state in states" v-bind:key="state">
      {{ state.name }}
      <br />
      {{ state.code }}
      <br />
      Median Household Income: {{ state.med_inc }}
      <br />
      Unemployment: {{ state.per_unemp_seas }}
      <br />
      Population in Metro: {{ state.per_pop_metro }}
      <br />
      Population High School Degree: {{ state.per_pop_high }}
    </h2>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      states: [],
    };
  },
  created: function () {
    axios.get("/api/states/").then((response) => {
      console.log("states index", response);
      this.states = response.data;
    });
  },
  methods: {},
};
</script>
