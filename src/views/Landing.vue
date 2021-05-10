<template>
  <div id="landing" class="landing-wrapper">
    <h1 @click="onClickHeadline()" class="headline-link">hannafreres</h1>
    <transition name="fade">
      <div
        v-if="showBackdrop"
        @click="onClickBackdrop()"
        class="backdrop"
        :class="{ 'backdrop--active': showBackdrop }"
      ></div>
    </transition>
  </div>
</template>

<script>
export default {
  name: "Landing",
  data() {
    return {
      showBackdrop: false,
    };
  },
  methods: {
    onClickHeadline: function (e) {
      this.$emit("clickedHeadline");
      this.showBackdrop = true;
    },
    onClickBackdrop: function (e) {
      this.$emit("clickedBackdrop");
      this.showBackdrop = false;
    },
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

    @include bp(desktop) {
      position: absolute;
      font-size: 75px;
      top: 30px;
      left: 75px;
      cursor: pointer;
    }
  }

  .backdrop {
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
  }
}
</style>