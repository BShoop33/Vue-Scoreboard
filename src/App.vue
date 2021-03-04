<template>
  <div id="app">
    <h1 class="header">Team 1 vs Team 2</h1>
    <h3 class="scoreStatus">The game is currently tied</h3>
    <div class="scores">
      <Team1 />
      <Team2 />
    </div>
  </div>
</template>



<script>
import Team1 from "./Team1.vue";
import Team2 from "./Team2.vue";

export default {
  components: {
    Team1,
    Team2,
  },
};
</script>

<style >
body {
  background-color: #2c3e50;
}

.header {
  color: hsla(0, 0%, 100%, 0.8);
  font-size: 8vw;
  margin-bottom: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: hsla(0, 0%, 100%, 0.8);
  margin-top: 60px;
}

.scores {
  display: flex;
  justify-content: space-evenly;
}

.scoreStatus {
  color: hsla(0, 0%, 100%, 0.6);
  width: 100%;
  text-align: center;
  font-size: 20px;
  margin-bottom: 40px;
  font-weight: 100;
}
</style>