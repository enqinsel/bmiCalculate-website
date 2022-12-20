<script setup>
import { ref } from "vue"
const props = defineProps(["data"]);
const data = parseFloat(props.data / 1000).toFixed(1)

console.log("result: ", data);

const category = ref(null)

if(data <= 18.5){
  category.value = "Zayıf"
}
else if(data <= 24.9){
  category.value = "Normal"
}
else if(data <= 29.9){
  category.value = "Fazla kilolu"
}
else if(data <= 40){
  category.value = "Obez"
}else{
  category.value = "Aşırı Obez"
}

</script>

<template>
  <div class="wrapper">
    <div class="result">
      <h1 class="result__title">BMI Sonuç</h1>
      <span class="result__data">{{ data }}</span>
    </div>
    <img src="../../assets/brackets.svg" />
    <div class="comment">
      <p class="comment__content">{{ category }}</p>
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
