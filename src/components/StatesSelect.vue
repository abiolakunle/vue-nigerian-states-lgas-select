<template>
  <v-container fluid grid-list-xl>
    <v-layout wrap align-center>
      <v-flex xs12 sm6 d-flex>
        <v-select
          :items="items"
          v-model="currentState"
          :label="label"
          :solo="solo"
          @change="handleStateChanged"
        ></v-select>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import statesData from "../data";
export default {
  props: {
    handleStateChanged: Function,
    label: { type: String, default: "Select a State" },
    solo: { type: Boolean, default: false },
    defaultState: { type: String },
  },
  data() {
    return {
      items: statesData.map((s) => s.name),
      currentState: this.defaultState,
    };
  },
};
</script>

<style>
</style>