<script setup>
import NavComp from "./components/Navbar/NavComp.vue";
import CalculateComp from "./components/Calculate/CalculateComp.vue";
</script>

<template>
  <img class="ath" src="./assets/athleteman.svg" alt="" />
  <img class="bgc" src="./assets/athletemanBackground.svg" alt="" />
  <NavComp></NavComp>
  <CalculateComp class="calculateComp"></CalculateComp>
</template>

<style scoped>
.ath {
  position: absolute;
  top: 50px;
  left: 750px;
  z-index: 1;
}
.bgc {
  position: absolute;
  top: 60px;
  left: 990px;
  z-index: 0;
}

.calculateComp {
  z-index: -2;
}
</style>
