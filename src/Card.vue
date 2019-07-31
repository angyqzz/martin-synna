<template>
  <div class="card-overlay">
    <div class="card">
      Hello
    </div>
  </div>
</template>
<script>
export default {
  name: "Card",
  props: [],
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
  z-index: 9999;
  display: flex;
  justify-content: center;
  align-items: center;
  .card {
    background: #fff;
    color: rgba(33, 33, 33, 1);
    width: 80%;
    margin: 0 auto;
    max-width: 400px;
  }
}
</style>
