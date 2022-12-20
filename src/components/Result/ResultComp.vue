<script setup>
const props = defineProps(["data"]);
const data = props.data / 1000;
console.log("result: ", data);
</script>

<template>
  <div class="wrapper">
    <div class="result">
      <h1 class="result__title">BMI Sonuç</h1>
      <span class="result__data">{{ data }}</span>
    </div>
    <img src="../../assets/brackets.svg" />
    <div class="comment">
      <p class="comment__content">Aşiri obez</p>
    </div>
  </div>
</template>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  gap: 3vh;
  width: 75vh;
  height: 18vh;
  margin-top: 1vh;
  margin-left: 6vh;
}

.result {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  justify-items: center;
  gap: 3vh;
}

.result__title {
  font-family: "Inter";
  font-style: normal;
  font-weight: 500;
  font-size: 3vh;
}

.result__data {
  font-family: "Inter";
  font-style: normal;
  font-weight: 500;
  font-size: 6vh;
}

img{
  height: 23vh;
}
.comment__content {
  font-family: "Inter";
  font-style: normal;
  font-weight: 200;
  line-height: 39px;
  font-size: 4vh;
  color: red;
}
</style>
