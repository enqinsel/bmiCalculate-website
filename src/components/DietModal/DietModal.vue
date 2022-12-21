<script setup>
const emits = defineEmits(["show"]);
const closeHandler = () => {
  emits("show");
};
</script>

<template>
  <div class="popup">
    <div class="popup__layer" @click="closeHandler"></div>
    <div class="popup__wrapper">
      <div class="header">
        <h1 class="name">Sana Uygun Olanı Seç!</h1>
      </div>
      <div class="content">
        <div class="pictures">
          <ul class="pictures__links">
            <li>
              <img class="linkImg" src="../../assets/dietOne.svg" />
            </li>
            <li>
              <img class="linkImg" src="../../assets/dietTwo.svg" />
            </li>
            <li>
              <img class="linkImg" src="../../assets/dietThree.svg" />
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">

.popup {
  position: fixed;
  z-index: 999;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  &__layer {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.549);
  }
  &__wrapper {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    padding: 10px;
    width: 800px;
    height: 500px;
    background-color: rgb(255, 255, 255);
    border-radius: 8px;
    box-shadow: rgba(130, 230, 8, 0.24) 1px 1px 20px 4px;
  }
}
.header {
  position: relative;
  width: 800px;
  height: 80px;
  border-bottom: 1px solid rgb(174, 174, 174);
}
.name {
  position: absolute;
  margin-top: 15px;
  font-size: 24px;
}
.content {
  width: 610px;
  height: auto;
  margin-top: 50px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 16px;
}
.pictures {
  position: relative;
  width: 600px;
  height: 350px;
  margin: 5px;
}
.pictures__links {
  padding: 5px;
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 40px;
}
.linkImg {
  width: 200px;
  height: 200px;
}

.linkImg:hover {
  position:absolute;
  top: 0;
  left: 0;
  bottom: 0;
  width: 300px;
  height: 300px;
  cursor: zoom-in;
}
</style>
