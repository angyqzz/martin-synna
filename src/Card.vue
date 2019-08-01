<template>
  <div
    class="card-overlay"
    :class="{'visible': visible}"
  >
    <div
      class="balloon"
      v-for="n in 10"
      :key="'balloon' + n"
    />
  </div>
</template>
<script>
export default {
  name: "Card",
  props: ["visible"],
  components: {},
  computed: {},
  methods: {},
  data() {
    return {};
  }
};
</script>
<style lang="less" scoped>
.card-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  z-index: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  .card {
    background: #fff;
    color: rgba(33, 33, 33, 1);
    width: 80%;
    margin: 0 auto;
    max-width: 400px;
    border-radius: 4px;
    padding: 16px;
    text-align: center;
  }

  .balloon {
    border-radius: 60%;
    background: red;
    display: block;
    height: 100px;
    opacity: 0.8;
    position: absolute;
    width: 80px;
    animation: flyingBalloon;
    animation-duration: 4s;
    animation-delay: 2s;
    animation-iteration-count: infinite;
    bottom: -20%;
    &:after {
      border-left: 5px solid transparent;
      border-right: 5px solid transparent;
      bottom: -5px;
      content: "";
      height: 9px;
      left: 45%;
      position: absolute;
      width: 0;
      border-bottom: 10px solid red;
    }

    &:nth-child(2) {
      left: 80%;
      animation-delay: 4s;
    }
    &:nth-child(3) {
      left: 20%;
      animation-delay: 1s;
    }
    &:nth-child(4) {
      left: 35%;
      animation-delay: 1.5s;
    }
    &:nth-child(5) {
      left: 10%;
      animation-delay: 2.2s;
    }
    &:nth-child(6) {
      left: 65%;
      animation-delay: 2.8s;
    }
    &:nth-child(7) {
      left: 51%;
      animation-delay: 2.6s;
    }
    &:nth-child(8) {
      left: 24%;
      animation-delay: 2.3s;
    }
    &:nth-child(9) {
      left: 43%;
      animation-delay: 3s;
    }
    &:nth-child(10) {
      left: 80%;
      animation-delay: 1.5s;
    }
  }

  @keyframes flyingBalloon {
    from {
      bottom: -20%;
    }
    to {
      bottom: 110%;
    }
  }
}
</style>
