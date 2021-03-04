<template>
  <div id="app">
    <div class="scores">
      <!-- binded class that renders team 1 with default formatting if team 1 is not winning or the winningTeamHeader
      formatting if team 1 is winning -->
      <h1
        :class="{
          winningTeamHeader: team1Winning,
          defaultTeamHeader: !team1Winning,
        }"
      >
        Team 1
      </h1>
      <h1 class="defaultTeamHeader">vs</h1>
      <!-- binded class that renders team 2 with default formatting if team 2 is not winning or the winningTeamHeader
      formatting if team 2 is winning -->
      <h1
        :class="{
          winningTeamHeader: team2Winning,
          defaultTeamHeader: !team2Winning,
        }"
      >
        Team 2
      </h1>
    </div>
    <h3 class="scoreStatus">{{ scoreStatus }}</h3>
    <div class="scores">
      <div class="team1Box">
        <p class="team1Score">{{ team1Score }}</p>
        <div class="buttons">
          <button
            class="subtractButton"
            @click="
              scoreDecrementTeam1();
              teamWinning();
            "
          >
            -
          </button>
          <button
            class="addButton"
            @click="
              scoreIncrementTeam1();
              teamWinning();
            "
          >
            +
          </button>
        </div>
      </div>
      <div class="team2Box">
        <p class="team2Score">{{ team2Score }}</p>
        <div class="buttons">
          <button
            class="subtractButton"
            @click="
              scoreDecrementTeam2();
              teamWinning();
            "
          >
            -
          </button>
          <button
            class="addButton"
            @click="
              scoreIncrementTeam2();
              teamWinning();
            "
          >
            +
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  /*defines the default state of the team1Score, team2Score, team1Winning, and team2Winning variables*/
  data() {
    return {
      team1Score: 0,
      team2Score: 0,
      team1Winning: false,
      team2Winning: false,
    };
  },

  methods: {
    /*When called, increments the team1Score variable by 1*/
    scoreIncrementTeam1() {
      this.team1Score += 1;
    },
    /*When called, decrements the team1Score variable by 1 unless the current value of team1Score is 0*/
    scoreDecrementTeam1() {
      if (this.team1Score == 0) {
        return 0;
      } else {
        this.team1Score -= 1;
      }
    },
    /*When called, increments the team2Score variable by 1*/
    scoreIncrementTeam2() {
      this.team2Score += 1;
    },
    /*When called, decrements the team2Score variable by 1 unless the current value of team2Score is 0*/
    scoreDecrementTeam2() {
      if (this.team2Score == 0) {
        return 0;
      } else {
        this.team2Score -= 1;
      }
    },
    /*When called, evaluates whether team1Score is greater than, less than, or equal to team2Score. If team1Score
    is greater than team2Score, it sets the value of the team1Winning value to the value 'true'. If team1Score is 
    less than team2 score, it sets the value of the team2Winning value to the value 'true'. If team1Score is equal
    to team2Score, it sets the value of both the team1Winning and team2Winning variables to false.*/
    teamWinning() {
      if (this.team1Score > this.team2Score) {
        this.team1Winning = true;
      } else if (this.team2Score > this.team1Score) {
        this.team2Winning = true;
      } else {
        (this.team1Winning = false), (this.team2Winning = false);
      }
    },
  },

  computed: {
    /*When called, evaluates whether team1Score is greater than, less than, or equal to team2Score. If team1Score
    is greater than team2Score, it returns a string explaining that relationship and listing the amount of points
    team 1 is winning by. If team1Score is less than team2 score, it returns a different string explaining that relationship 
    and listing the amount of points team 2 is winning by. If team1Score is equal to team2Score, it returns a third string 
    explaining the score is tied.*/
    scoreStatus() {
      const score =
        this.team1Score > this.team2Score
          ? `Team 1 is leading by ${this.team1Score - this.team2Score} points`
          : this.team2Score > this.team1Score
          ? `Team 2 is leading by ${this.team2Score - this.team1Score} points`
          : "The game is currently tied";
      return score;
    },
  },
};
</script>

<style >
.addButton {
  background-color: rgba(0, 255, 0, 0.1);
  border: 5px solid rgba(0, 255, 0, 0.4);
  color: hsla(0, 0%, 100%, 0.8);
  cursor: pointer;
  font-size: 3vw;
  height: 100%;
  width: 50%;
}

#app {
  color: hsla(0, 0%, 100%, 0.8);
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-top: 60px;
  text-align: center;
}

body {
  background-color: #2c3e50;
}

.buttons {
  bottom: 5%;
  height: 20%;
  left: 10%;
  position: absolute;
  text-align: center;
  width: 80%;
}

.defaultTeamHeader {
  color: hsla(0, 0%, 100%, 0.8);
  font-size: 8vw;
  margin-bottom: 0;
}

.leading {
  color: #daa520;
}

.scores {
  display: flex;
  justify-content: space-evenly;
}

.scoreStatus {
  color: hsla(0, 0%, 100%, 0.6);
  font-size: 20px;
  font-weight: 100;
  margin-bottom: 40px;
  text-align: center;
  width: 100%;
}

.subtractButton {
  background-color: rgba(255, 0, 0, 0.1);
  border: 5px solid rgba(255, 0, 0, 0.4);
  color: hsla(0, 0%, 100%, 0.8);
  cursor: pointer;
  font-size: 3vw;
  height: 100%;
  width: 50%;
}

.team1Box {
  border: 10px solid hsla(0, 0%, 100%, 0.8);
  color: hsla(0, 0%, 100%, 0.8);
  content: "";
  display: block;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-top: 60px;
  padding-bottom: 20%;
  position: relative;
  text-align: center;
  width: 25%;
}

.team1Score {
  font-size: 8vw;
  left: 50%;
  margin: 0;
  position: absolute;
  top: 50%;
  transform: translate(-50%, -50%);
}

.team2Box {
  border: 10px solid hsla(0, 0%, 100%, 0.8);
  color: hsla(0, 0%, 100%, 0.8);
  content: "";
  display: block;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-top: 60px;
  padding-bottom: 20%;
  position: relative;
  text-align: center;
  width: 25%;
}

.team2Score {
  font-size: 8vw;
  left: 50%;
  margin: 0;
  position: absolute;
  top: 50%;
  transform: translate(-50%, -50%);
}

.winningTeamHeader {
  color: #daa520;
  font-size: 8vw;
  margin-bottom: 0;
}
</style>