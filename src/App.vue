<template>
  <div class="desktopWarning">
    <h1>
      Версия для компьютеров находится в разработке, <br />
      для более приятного интерфейса продолжите на телефоне
    </h1>
    <h4>Постараюсь как можно быстрее закончить ее, обещаю 🐣</h4>
  </div>

  <GridRow />
  <!-- <timeTable /> -->
</template>

<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup

import GridRow from "./components/gridRow.vue";
// import timeTable from "./components/timetable.vue";
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  margin: 1rem 6%;

  @media (prefers-color-scheme: dark) {
    color: #ffffff;
  }
}

body{
    @media (prefers-color-scheme: dark) {
      background-color: #121212;
  }
}

.desktopWarning {
  display: none;
  width: 100%;
  height: 50vh;
  // position: absolute;
  // top: 0;
  // left: 0;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: #fff;

  overflow: hidden;

  h1 {
    font-size: 2rem;
    margin: 0 10%;
  }

    @media (prefers-color-scheme: dark) {
      background-color: #121212;
  }

  @media (min-width: 1200px) {
    display: flex;
  }

  @media (max-width: 1199px) {
    display: none;
  }
}
</style>
