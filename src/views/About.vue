<template>
  <div id="about" class="about-wrapper">
    <h1 class="headline-about">about</h1>
    <div @click="onClickCircle" class="nav-circle"></div>
  </div>
</template>

<script>
export default {
  name: "About",
  methods: {
    onClickCircle: function (e) {
      this.$emit("clickedCircle");
    },
  },
};
</script>

<style lang="scss">
.about-wrapper {
  height: 100vh;
  widows: 100vw;
  background: black;

  .headline-about {
    margin: 0;
    padding: 15px 0;
    color: white;
  }

  .nav-circle {
    height: 20px;
    width: 20px;
    background-color: white;
    border-radius: 50%;
    position: absolute;
    top: 25px;
    right: 25px;
    cursor: pointer;
  }
}
</style>