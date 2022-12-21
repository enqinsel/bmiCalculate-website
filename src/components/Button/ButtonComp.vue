<script setup>
import { ref } from "vue";

const props = defineProps(["showGender", "showOtherButtons", "showDiet", "disable"]);
const emits = defineEmits(["calcHandler", "dietHandler"]);

const calcAfter = ref(null);

const calculateHandler = () => {
  emits("calcHandler");
  calcAfter.value = "calcAfter";
};

const dietHandler = () => {
  emits("dietHandler");
};


</script>

<template>
  <!-- Input Comp olarak ayır -->
  <div class="gender" v-if="props.showGender">
    <label class="rad-label">
      <input type="radio" class="manInput" name="gender" />
      <div class="manDesign"></div>
    </label>

    <label class="rad-label">
      <input type="radio" class="womanInput" name="gender" />
      <div class="womanDesign"></div>
    </label>
  </div>

  <div class="otherButton" v-if="props.showOtherButtons">
    <button
      @click="calculateHandler"
      class="calc"
      :class="calcAfter"
      :disabled="props.disable"
    >
      HESAPLA
    </button>
    <button @click="dietHandler" v-if="props.showDiet" class="list">
      Diyet Listesini Gör
    </button>
    
  </div>
</template>

<style scoped>

.calc {
  position: absolute;
  left: 200px;
  width: 175px;
  height: 65px;
  font-size: 25px;
  color: rgb(0, 0, 0);
  background: linear-gradient(90deg, #d9fda9 3.43%, #64feb8 93.67%);
  border-radius: 6px;
}

.calc:hover {
  background: linear-gradient(90deg, #e2f6c7fb 3.43%, #b3f9d9 93.67%);
  cursor: pointer;
}

.calcAfter {
  position: absolute;
  top: 465px;
  left: 80px;
  width: 150px;
  height: 50px;
  font-size: 20px;
  color: rgb(255, 255, 255);
  background: rgb(0, 49, 2);
  border-radius: 6px;
}

.calcAfter:hover{
  background: rgb(0, 49, 2);
  cursor: pointer;
}

.list {
  position: absolute;
  left: 300px;
  width: 275px;
  height: 75px;
  font-size: 25px;
  color: rgb(255, 255, 255);
  background: linear-gradient(90deg, #f4743d 3.43%, #d6ed40 93.67%);
  border-radius: 6px;

  animation: blinker 2s linear infinite;
}
.list:hover {
  opacity: 100;
  animation: blinker 2s;
  cursor: pointer;
}

@keyframes blinker {
  50% {
    opacity: 0;
  }
}

.gender {
  display: flex;
  flex-direction: row;
  margin-left: 190px;
  gap: 75px;
}

.womanDesign {
  width: 50px;
  height: 50px;
  padding: 8px;
  border-radius: 100px;
  background: linear-gradient(to right bottom, hsl(154, 97%, 62%), hsl(225, 97%, 62%));
  position: relative;
}

.womanDesign::before {
  content: "";

  display: inline-block;
  width: inherit;
  height: inherit;
  border-radius: inherit;
  background: hsl(0, 0%, 90%);
  transform: scale(1.1);
  transition: 0.3s;
  background: black;
  background-image: url("../../assets/womanButton.svg");
  background-repeat: no-repeat;
}
.manDesign {
  width: 50px;
  height: 50px;
  padding: 8px;
  border-radius: 100px;
  background: linear-gradient(to right bottom, hsl(154, 97%, 62%), hsl(225, 97%, 62%));
  position: relative;
}

.manDesign::before {
  content: "";

  display: inline-block;
  width: inherit;
  height: inherit;
  border-radius: inherit;
  background: hsl(0, 0%, 90%);
  transform: scale(1.1);
  transition: 0.3s;
  background: black;
  background-image: url("../../assets/manButton.svg");
  background-repeat: no-repeat;
}

.womanInput:checked + .womanDesign::before {
  transform: scale(0);
}

.manInput:checked + .manDesign::before {
  transform: scale(0);
}

.rad-label {
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 100px;

  cursor: pointer;
  transition: 0.3s;
}

.rad-label:hover,
.rad-label:focus-within {
  background: hsla(0, 0%, 80%, 0.14);
}

.womanInput {
  position: absolute;
  left: 0;
  top: 0;
  width: 1px;
  height: 1px;
  opacity: 0;
  z-index: -1;
}
.manInput {
  position: absolute;
  left: 0;
  top: 0;
  width: 1px;
  height: 1px;
  opacity: 0;
  z-index: -1;
}

.womanInput:checked + .womanDesign::before {
  transform: scale(0);
}

.manInput:checked + .manDesign::before {
  transform: scale(0);
}

.womanInput:checked {
  color: hsl(0, 0%, 40%);
}
.manInput:checked {
  color: hsl(0, 0%, 40%);
}
</style>
