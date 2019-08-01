<template>
  <div id="app">
    <div class="card-title">Eat all the slices!</div>
    <div class="card-text">Click on each slice to destroy it 😀</div>
    <div class="plate">
      <div class="cake">
        <div v-for="n in 8" class="cake-slice" @click="setEaten(n)" :key="n"></div>
        <div class="cake-decoration">
          <div class="slice-borders">
            <div v-for="n in 4" :key="'border' + n"></div>
          </div>
          <span>
            Happy
            <br />Birthday
          </span>
        </div>
      </div>
      <div class="cake cake-mask" v-show="!gameFinished">
        <div v-for="n in 8" class="cake-slice" :class="{'hidden' : hidden[n]}" :key="n"></div>
      </div>
      <div class="button" v-show="gameFinished" @click="showCard = true">
        <div class="martin-photo" :class="{'visible': gameFinished}"></div>
      </div>
    </div>
    <card :visible="showCard" />

    <div class="footer">Made with care ❤️ by Angie</div>
  </div>
</template>

<script>
import Vue from "vue";
import moment from "moment";
import Card from "./Card";

let timerSetter = null;
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
    finishGame() {
      this.gameFinished = true;
    },
    setEaten(n) {
      if (this.hidden[n]) {
        return;
      }

      let values = Object.keys(this.hidden);
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
      showCard: false
    };
  }
};
</script>

<style lang="less">
@import "style.less";
</style>
