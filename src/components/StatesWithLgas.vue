<template>
  <v-app>
    <StatesSelect
      :solo="solo"
      :label="stateLabel"
      :handleStateChanged="handleStateChanged"
    />
    <LocalGovtSelect
      :handleLgaChanged="handleLgaChanged"
      :solo="solo"
      :label="lgaLabel"
      :state="state"
    />
  </v-app>
</template>

<script>
import StatesSelect from "./StatesSelect";
import LocalGovtSelect from "./LocalGovtSelect";
//import StatesData from "../data";

export default {
  components: { StatesSelect, LocalGovtSelect },
  props: {
    stateLabel: { type: String, default: "Select a State" },
    lgaLabel: { type: String, default: "Select a Lga" },
    defaultState: { type: String },
    handleSelectChanged: Function,
  },
  name: "App",
  data() {
    return {
      solo: true,
      state: this.defaultState,
      lga: undefined,
    };
  },
  methods: {
    handleStateChanged(state) {
      this.state = state;
      this.handleSelectChanged(this.state, this.lga);
    },
    handleLgaChanged(lga) {
      this.lga = lga;
      this.handleSelectChanged(this.state, this.lga);
    },
  },
};
</script>
