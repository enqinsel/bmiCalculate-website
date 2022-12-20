<script setup></script>

<template>
  <div class="container">
    <div class="content">
      <div class="logo">
        <a href="">
          <img src="../../assets/logo.svg" alt="logo" />
        </a>
      </div>
      <div class="links">
        <ul>
            <li>
                <a href="">BMI Hesapla</a>
            </li>
            <li>
                <a href="">BMI Nedir</a>
            </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  width: 100%;
  background-color: #000;

  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

.content{
    width: 150vh;
    /* background: rgb(155, 208, 20); */
    padding: 1vh;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
}

.logo{
    margin-left: 15vh;
}

.links ul{
    display: flex;
    flex-direction: row;
    gap: 10vh;
    padding: 1vh;
}

a{
    color: white;
    text-decoration: none;
}
</style>
