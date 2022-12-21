<script setup>
import { onMounted, ref } from "vue";
import NavComp from "./components/Navbar/NavComp.vue";
import CalculateComp from "./components/Calculate/CalculateComp.vue";


const rightItem = ref();

onMounted(() => {
  setInterval(function () {
    rightItem.value += -500;
    if ((rightItem.value = -1500)) {
      clearInterval();
    }
  }, 100);
});
</script>

<template>
  <img
    :style="`transform: translateX(${rightItem}px)`"
    class="ath"
    src="./assets/athleteman.svg"
  />
  <img
    :style="`transform: translateX(${rightItem}px)`"
    class="bgc"
    src="./assets/athletemanBackground.svg"
  />

  <NavComp></NavComp>
  <CalculateComp></CalculateComp>
</template>

<style scoped>
.ath {
  position: absolute;
  top: 50px;
  left: 2200px;
  transition: all 1s ease;
  z-index: 1;
}
.bgc {
  position: absolute;
  top: 60px;
  left: 2450px;
  transition: all 1s ease;
  z-index: 0;
}

/* .calsculateComp {
  z-index: -2;
} */


</style>
