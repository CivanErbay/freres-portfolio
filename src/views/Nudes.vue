<template>
  <div class="nudes-wrapper">
    <h2 class="headline-nudes">Nudes</h2>
    <div @click="onClickCircle" class="nav-circle"></div>
  </div>
</template>

<script>
export default {
  name: "Nudes",
  methods: {
    onClickCircle: function (e) {
      this.$emit("clickedCircle");
      /* this.showBackdrop = true; */
    },
  },
};
</script>

<style lang="scss" scoped>
.nudes-wrapper {
  height: 100vh;
  widows: 100vw;
  background: black;

  .headline-nudes {
    margin: 0;
    color: white;
  }

  .nav-circle {
    height: 20px;
    width: 20px;
    background-color: white;
    border-radius: 50%;
    position: absolute;
    top: 20px;
    right: 25px;
    cursor: pointer;
  }
}
</style>