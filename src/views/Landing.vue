<template>
  <div id="landing" class="landing-wrapper">
    <h1 @click="onClickHeadline()" class="headline-link">hannafreres</h1>
  </div>
</template>

<script>
export default {
  name: "Landing",
  data() {
    return {
      showBackdrop: false,
      isMobile: false,
    };
  },
  methods: {
    onClickHeadline: function (e) {
      this.$emit("clickedHeadline");
      this.showBackdrop = true;
    },
  },

  mounted() {
    if (window.innerWidth < 768) this.isMobile = true;
  },
};
</script>

<style lang="scss">
@import "../scss/breakpoints.scss";

.landing-wrapper {
  background: url("../assets/nd_010.jpg") no-repeat 0 0;
  background-position: center;
  background-size: cover;
  position: relative;
  width: 100vw;
  height: 100vh;
  padding: 0;
  margin: 0;

  @include bp(phablet) {
    background: url("../assets/nd_011.jpg") no-repeat 0 0;
    background-position: center;
    background-size: cover;
  }

  @include bp(tablet) {
    background: url("../assets/nd_005.jpg") no-repeat 0 0;
    background-position: center;
    background-size: cover;
  }

  .headline-link {
    position: absolute;
    color: white;
    font-weight: 300;
    top: 30px;
    left: 40px;
    letter-spacing: 7px;
    opacity: 0.7;
    font-size: 25px;
    cursor: pointer;

    @include bp(phablet) {
      font-size: 38px;
      left: 90px;
      top: 85px;
      color: white;
    }

    @include bp(tablet) {
      font-size: 55px;
      left: 70px;
      top: 40px;
      color: white;
    }

    @include bp(laptop) {
      font-size: 80px;
      left: 70px;
      top: 40px;
    }

    @include bp(desktop) {
      font-size: 100px;
      left: 100px;
      top: 60px;
      cursor: pointer;
    }
  }
}
</style>