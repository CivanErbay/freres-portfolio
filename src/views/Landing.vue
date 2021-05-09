<template>
  <div id="landing" class="landing-wrapper">
    <h1 @click="onClickHeadline()" class="headline-link">hannafreres</h1>
    <transition name="fade">
      <div
        v-if="showBackdrop"
        @click="onClickBackdrop()"
        class="backdrop"
        :class="{'backdrop--active': showBackdrop}"
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
.landing-wrapper {
  padding: 0;
  margin: 0;
  width: 100vw;
  height: 100vh;
  background: url("../assets/img1.jpeg") no-repeat 0 0;
  background-position: center;
  background-size: cover;
  position: relative;

  .headline-link {
    position: absolute;
    font-weight: 300;
    font-size: 75px;
    color: white;
    top: 30px;
    left: 75px;
    cursor: pointer;
  }

  .backdrop {
    width: 100vw;
    height: 100vh;
    z-index: 1;
    background-color: rgba($color: #000000, $alpha: 0.8);
    transition: opacity 0.5s ease-in;

   /*  &--active {
      opacity: 0.8;
    } */
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