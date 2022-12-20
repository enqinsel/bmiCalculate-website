<script setup>
import ButtonComp from "../Button/ButtonComp.vue";
import { ref } from "vue";
import ResultComp from "../Result/ResultComp.vue";

const rangeWeight = ref(0);
const marginWeight = ref(null);
const rangeHeight = ref(0);
const marginHeight = ref(null);
const showDiet = ref(false);
const disabledCalc = ref(false);
const data = ref();
const showResult = ref();

function calculateBMI(height, weight) {

  const dividedHeight = height / 100;

  const  result = weight / (dividedHeight * dividedHeight);
  if(isNaN(result) === true){
    data.value = 0
  }else{
    data.value = result
  }
  
  return result
}

const weightHandler = (e) => {
  rangeWeight.value = e.target.value;
  marginWeight.value = e.target.value * 1.9;
};

const heightHandler = (e) => {
  rangeHeight.value = e.target.value;
  marginHeight.value = e.target.value * 1.9;
};

const calcHandler = () => {
  showDiet.value = true;
  disabledCalc.value = true;
  showResult.value = true;
  calculateBMI(rangeHeight.value, rangeWeight.value);
};

const dietHandler = () => {
  console.log("asdf");
};
</script>

<template>
  <div class="container">
    <div class="content">
      <div class="row">
        <ButtonComp :showGender="true" :showOtherButtons="false"></ButtonComp>
      </div>
      <div class="calc">
        <div class="height">
          <div class="stick">
            <span :style="`left:${marginHeight}px`" id="rs-bullet" class="rs-label"
              >{{ rangeHeight }}
              <span style="font-size: 2.5vh; display: block">cm</span></span
            >
            <input
              @input="heightHandler"
              id="rs-range-line"
              class="rs-range"
              type="range"
              value="0"
              min="0"
              max="230"
            />
          </div>
          <img src="" alt="" />
        </div>
        <div class="weight">
          <div class="stick">
            <span :style="`left:${marginWeight}px`" id="rs-bullet" class="rs-label"
              >{{ rangeWeight }}
              <span style="font-size: 2.5vh; display: block">kg</span></span
            >
            <input
              @input="weightHandler"
              id="rs-range-line"
              class="rs-range"
              type="range"
              value="0"
              min="0"
              max="230"
            />
          </div>
          <img src="" alt="" />
        </div>
      </div>
      <div class="otherButtons">
        <ButtonComp
          @dietHandler="dietHandler"
          @calcHandler="calcHandler"
          :showGender="false"
          :showOtherButtons="true"
          :showDiet="showDiet"
          :disable="disabledCalc"
        ></ButtonComp>
      </div>
    </div>
  </div>
      <ResultComp class="resultComp" v-if="showResult" :data="data"></ResultComp>
</template>

<style scoped>

.container {
  width: 100%;
  background: rgb(0, 0, 0);
  height: 72vh;
}

.content {
  width: 150vh;
  height: auto;
  /* background: rgba(225, 255, 0, 0.655); */
}

.row {
  display: flex;
  flex-direction: row;
  padding: 1vh;
}

.calc {
  width: 100vh;
  /* background: rgb(87, 198, 19); */
  padding: 1vh;
}

.height {
  display: grid;
  grid-template-columns: repeat(1 1fr);
  /* background-color: aqua; */
}

.stick {
  width: auto;
  padding-left: 50px;
  padding-bottom: 40px;
}

.rs-range {
  margin-top: 29px;
  width: 460px;
  -webkit-appearance: none;
}

.rs-range::-moz-range-track {
  width: 100%;
  height: 1px;
  cursor: pointer;
  box-shadow: none;
  background: #ffffff;
}
.rs-range::-webkit-slider-thumb {
  box-shadow: none;
  border: 0px solid #ffffff;
  box-shadow: 0px 10px 10px rgba(0, 0, 0, 0.25);
  height: 42px;
  width: 22px;
  border-radius: 22px;
  background: rgba(255, 255, 255, 1);
  cursor: pointer;
  -webkit-appearance: none;
  margin-top: -20px;
}

.rs-range::-moz-range-thumb {
  box-shadow: none;
  border: 0px solid #ffffff;
  box-shadow: 0px 10px 10px rgba(0, 0, 0, 0.25);
  height: 42px;
  width: 22px;
  border-radius: 22px;
  background: rgba(255, 255, 255, 1);
  cursor: pointer;
  -webkit-appearance: none;
  margin-top: -20px;
}
.rs-range::-moz-focus-outer {
  border: 0;
}
.rs-range::-webkit-slider-runnable-track {
  width: 100%;
  height: 1px;
  cursor: pointer;
  box-shadow: none;
  background: #ffffff;
  border-radius: 0px;
  border: 0px solid #010101;
}

.rs-range:focus {
  outline: none;
}
.rs-label {
  position: relative;
  transform-origin: center center;
  display: block;
  width: 68px;
  height: 68px;
  background: transparent;
  border-radius: 50%;
  line-height: 30px;
  text-align: center;
  font-weight: bold;
  padding-top: 1vh;
  box-sizing: border-box;
  border: 2px solid #fff;
  margin-left: -20px;
  left: attr(value);
  color: #fff;
  font-style: normal;
  font-weight: normal;
  line-height: normal;
  font-size: 3vh;
}
.rs_label::after {
  content: "kg";
  display: block;
  font-size: 20px;
  letter-spacing: 0.07em;
  margin-top: -2px;
}
</style>
