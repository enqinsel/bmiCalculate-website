<script setup>
import { onMounted, ref } from "vue";

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
    src="../../assets/athleteman.svg"
  />
  <img
    :style="`transform: translateX(${rightItem}px)`"
    class="bgc"
    src="../../assets/athletemanBackground.svg"
  />
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
</style>
