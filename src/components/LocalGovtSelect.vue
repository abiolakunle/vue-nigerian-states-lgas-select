<template>
  <v-container fluid grid-list-xl>
    <v-layout wrap align-center>
      <v-flex xs12 sm6 d-flex>
        <v-select
          v-model="currentLga"
          :items="items"
          :label="label"
          :solo="solo"
          @change="handleLgaChanged"
        ></v-select>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import statesData from "../data";
export default {
  props: {
    state: { type: String, default: statesData[0].name },
    label: { type: String, default: "Select a Lga" },
    solo: { type: Boolean, default: false },
    handleLgaChanged: Function,
  },
  data() {
    return {
      currentLga: statesData
        .find((s) => s.name === this.state)
        .locals.map((s) => s.name)[0],
    };
  },
  methods: {},
  computed: {
    items() {
      return statesData
        .find((s) => s.name === this.state)
        .locals.map((s) => s.name);
    },
  },
  watch: {
    state: {
      immediate: true,
      deep: true,
      handler(newValue, oldValue) {
        if (newValue !== oldValue && oldValue !== undefined) {
          this.currentLga = statesData
            .find((s) => s.name === newValue)
            .locals.map((s) => s.name)[0];
          this.handleLgaChanged(this.currentLga);
        }
      },
    },
  },
};
</script>

<style>
</style>