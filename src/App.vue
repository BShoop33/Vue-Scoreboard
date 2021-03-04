<template>
  <div id="app">
    <h1 class="header">Team 1 vs Team 2</h1>
    <h3 class="scoreStatus">{{ scoreStatus }}</h3>
    <div class="scores">
      <div class="team1Box">
        <p class="team1Score" :sco="team1Score">{{ team1Score }}</p>
        <div class="buttons">
          <button class="subtractButton" @click="scoreDecrementTeam1">-</button>
          <button class="addButton" @click="scoreIncrementTeam1">+</button>
        </div>
      </div>
      <div class="team2Box">
        <p class="team2Score">{{ team2Score }}</p>
        <div class="buttons">
          <button class="subtractButton" @click="scoreDecrementTeam2">-</button>
          <button class="addButton" @click="scoreIncrementTeam2">+</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      team1Score: 0,
      team2Score: 0,
    };
  },
  methods: {
    scoreIncrementTeam1() {
      this.team1Score += 1;
    },
    scoreDecrementTeam1() {
      if (this.team1Score == 0) {
        return 0;
      } else {
        this.team1Score -= 1;
      }
    },
    scoreIncrementTeam2() {
      this.team2Score += 1;
    },
    scoreDecrementTeam2() {
      if (this.team2Score == 0) {
        return 0;
      } else {
        this.team2Score -= 1;
      }
    },
  },
  computed: {
    scoreStatus() {
      const score =
        this.team1Score > this.team2Score
          ? `Team 1 is leading by ${this.team1Score - this.team2Score} point`
          : this.team2Score > this.team1Score
          ? `Team 2 is leading by ${this.team2Score - this.team1Score}`
          : "The game is currently tied";
      return score;
    },
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

.team1Box {
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

.team1Score {
  margin: 0;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 8vw;
}

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