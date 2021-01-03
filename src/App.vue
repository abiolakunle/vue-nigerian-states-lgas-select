<template>
  <v-app>
    <StatesSelect :handleStateChanged="handleStateChanged" />
    <LocalGovtSelect :handleLgaChanged="handleLgaChanged" :state="state" />
    <StatesWithLgas :handleSelectChanged="handleSelectChanged" />
  </v-app>
</template>

<script>
import { StatesSelect, LocalGovtSelect, StatesWithLgas } from "./components";
export default {
  components: { StatesSelect, LocalGovtSelect, StatesWithLgas },
  name: "App",
  data() {
    return { state: undefined };
  },
  methods: {
    handleStateChanged(state) {
      this.state = state;
    },
    handleLgaChanged() {},
    handleSelectChanged(state, lga) {
      console.log("State & lga", state, lga);
    },
  },
};
</script>
