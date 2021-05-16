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
  background: url("../assets/img3.jpeg") no-repeat 0 0;
  background-position: center;
  background-size: cover;
  position: relative;
  width: 100vw;
  height: 100vh;
  padding: 0;
  margin: 0;

  @include bp(phablet) {
    background: url("../assets/img4.jpeg") no-repeat 0 0;
    background-position: center;
    background-size: cover;
  }

  @include bp(tablet) {
    background: url("../assets/img1.jpeg") no-repeat 0 0;
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

    /* &:before {
      content: "";
      width: 99px;
      height: 1px;
      background-color: white;
      display: block;
      position: relative;
      bottom: -44px;
    } */
  }

  /*  .backdrop {
    width: 100vw;
    height: 100vh;
    z-index: 1;
    background-color: rgba($color: #000000, $alpha: 0.8);
    transition: opacity 0.5s ease-in;
  }

  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 0.5s;
  }
  .fade-enter,
  .fade-leave-to {
    opacity: 0.5;
  } */
}
</style>