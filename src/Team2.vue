<template>
  <div class="team2Box">
    <p class="team2Score">0</p>
    <div class="buttons">
      <button class="subtractButton">-</button>
      <button class="addButton">+</button>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.team2Box {
  position: relative;
  width: 25%;
  border: 10px solid hsla(0, 0%, 100%, 0.8);

  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: hsla(0, 0%, 100%, 0.8);
  margin-top: 60px;

  content: "";
  display: block;
  padding-bottom: 20%;
}

.team2Score {
  margin: 0;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 8vw;
}

.buttons {
  position: absolute;
  bottom: 5%;
  left: 10%;
  text-align: center;
  height: 20%;
  width: 80%;
}

.subtractButton {
  height: 100%;
  width: 50%;
  font-size: 3vw;
  color: hsla(0, 0%, 100%, 0.8);
  cursor: pointer;
  border: 5px solid rgba(255, 0, 0, 0.4);
  background-color: rgba(255, 0, 0, 0.1);
}

.addButton {
  height: 100%;
  width: 50%;
  font-size: 3vw;
  color: hsla(0, 0%, 100%, 0.8);
  cursor: pointer;
  border: 5px solid rgba(0, 255, 0, 0.4);
  background-color: rgba(0, 255, 0, 0.1);
}
</style>