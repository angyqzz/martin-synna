<template>
  <div id="app">
    <div class="card-title">Eat all the slices!</div>
    <div class="card-text">Click on each slice to destroy it 😀</div>
    <div class="plate">
      <div class="cake">
        <div
          v-for="n in 6"
          class="cake-slice"
          :class="{'hidden' : hidden[n]}"
          @click="setEaten(n)"
          :key="n"
        ></div>
        <div class="cake-decoration">Happy <br /> Birthday</div>
      </div>
    </div>
    <card />
  </div>
</template>

<script>
import Vue from "vue";
import Card from "./Card";
export default {
  name: "app",
  components: {
    Card
  },
  methods: {
    setEaten(n) {
      Vue.set(this.hidden, n, true);
    }
  },
  data() {
    return {
      hidden: {}
    };
  }
};
</script>

<style lang="less">
@import "style.less";
</style>
