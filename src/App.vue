<template>
  <div id="app">
    <card v-show="gameFinished"></card>
    <div class="card-title">
      {{gameFinished ? 'Woop, woop! Happy Birthday!' : 'Eat all the slices!'}}
    </div>
    <div
      v-if="gameFinished"
      class="card-text"
    >
      Wow, it took you only a {{duration}} seconds to finish that cake! <span
        v-if="bestTime !== 1000000"
        :class="{'achived' : this.duration < this.bestTime}"
      >(Best time: {{bestTime}})</span>
    </div>
    <div
      class="card-text"
      v-else
    >Click on each slice to destroy it 😀</div>
    <div class="plate">
      <div class="cake">
        <div
          v-for="n in 8"
          class="cake-slice"
          @click="setEaten(n)"
          :class="{'eaten' : hidden[n]}"
          :key="n"
        ></div>
        <div class="cake-decoration">
          <div class="slice-borders">
            <div
              v-for="n in 4"
              :key="'border' + n"
            ></div>
          </div>
          <span>
            Happy
            <br />Birthday
          </span>
        </div>
      </div>
      <div
        class="cake cake-mask"
        v-show="!gameFinished"
      >
        <div
          v-for="n in 8"
          class="cake-slice"
          :class="{'hidden' : hidden[n]}"
          :key="n"
        ></div>
      </div>
      <div
        class="button"
        v-show="gameFinished"
      >
        <div
          class="martin-photo"
          :class="{'visible': gameFinished}"
        ></div>
      </div>
    </div>
    <div
      v-if="gameFinished"
      @click="restartGame()"
      class="restart-game"
    >Nah, I can do better!</div>
    <div class="footer">Baked with care ❤️ by Angie</div>
  </div>
</template>

<script>
import Vue from "vue";
import moment from "moment";
import Card from "./Card";

let timerSetter = null;

let start;
let end;

export default {
  name: "app",
  components: {
    Card
  },
  methods: {
    generateRandomStyle(n) {
      console.log(n);
      let bottom,
        left = null;

      left = Math.floor(Math.random() * 150) + 100;
      bottom = Math.floor(Math.random() * 100) + 30;

      return {
        left: left + "px",
        top: top + "px"
      };
    },
    restartGame() {
      this.hidden = {};
      start, (end = null);
      this.gameFinished = false;
    },
    startGame() {
      start = moment();
    },
    finishGame() {
      this.gameFinished = true;
      end = moment();

      this.duration = end.diff(start, "seconds", true);

      if (localStorage.getItem("bestTime")) {
        this.bestTime = localStorage.getItem("bestTime");
      }

      if (this.duration < this.bestTime) {
        localStorage.setItem("bestTime", this.duration);
      }
    },
    setEaten(n) {
      if (this.hidden[n]) {
        return;
      }

      let values = Object.keys(this.hidden);

      if (values.length === 1) {
        this.startGame();
      }

      Vue.set(this.hidden, n, true);

      if (values.length == 7) {
        this.finishGame();
      }
    }
  },
  data() {
    return {
      hidden: {},
      gameFinished: false,
      showCard: false,
      duration: null,
      bestTime: 1000000
    };
  }
};
</script>

<style lang="less">
@import "style.less";
</style>
