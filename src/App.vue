<template>
  <div id="app">
    <div class="nav" :class="{ 'nav--active': navActive }">
      <a class="nudes">nudes</a>
      <a class="portraits">portraits</a>
      <a class="space">space</a>
      <a class="about">about</a>
      <button class="close-button" v-if="isMobile" @click="navActive = false">
        <div class="close-circle"></div>
      </button>
    </div>
    <Landing
      @clickedHeadline="navActive = true"
      @clickedBackdrop="navActive = false"
    ></Landing>
  </div>
</template>

<script>
import Landing from "./views/Landing.vue";

export default {
  name: "App",
  components: { Landing },
  data() {
    return {
      navActive: false,
      isMobile: false,
    };
  },
  methods: {},
  mounted() {
    if (window.innerWidth < 768) this.isMobile = true;
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;700&display=swap");
@import "./scss/breakpoints.scss";

:root {
  --font: Open-sans, sans-serif;
  --textColor: #374961;
  --linkActiveColor: #41b783;
}
body {
  padding: 0;
  margin: 0;
}
#app {
  font-family: var(--font);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: var(--textColor);
}

.nav {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: flex-start;
  z-index: 2;
  background-color: black;
  height: 100vh;
  width: 100%;
  transition: ease-out 0.9s;
  transform: translateX(-100%);
  position: absolute;

  .close-button {
    border: none;
    background-color: black;
    bottom: 20px;
    right: 20px;
    position: absolute;
  }

  .close-circle {
    width: 35px;
    height: 35px;
    border: solid white 5px;
    border-radius: 50%;
  }

  @include bp(phablet) {
    transform: translateY(-100%);
    height: 450px;
    flex-direction: row;
    justify-content: flex-start;
    align-items: center;
  }

  &--active {
    transform: translateY(0);
  }

  a {
    font-weight: bold;
    font-size: 36px;
    color: white;
    margin: 0 35px;
    text-decoration: none;
    cursor: pointer;

    &:first-child {
      @include bp(phablet) {
        margin-left: 150px;
      }
    }

    &:last-of-type {
      margin: 0;
    }

    &.about {
      right: 20px;
      top: 20px;
      font-size: 30px;
      position: absolute;
    }
  }

  .nudes:after {
    content: "";
    width: 5px;
    height: 80px;
    background-color: white;
    display: inline-block;
    position: relative;
    left: -114px;

    @include bp(phablet) {
      width: 80px;
      height: 4px;
      display: block;
      bottom: -40px;
      left: unset;
    }
  }
  .portraits:after {
    content: "";
    width: 5px;
    height: 70px;
    background-color: white;
    display: inline-block;
    position: relative;
    left: -154px;

    @include bp(phablet) {
      width: 70px;
      height: 4px;
      display: block;
      bottom: -20px;
      left: unset;
    }
  }
  .space:after {
    content: "";
    width: 5px;
    height: 50px;
    background-color: white;
    display: inline-block;
    position: relative;
    left: -110px;

    @include bp(phablet) {
      left: unset;
      width: 50px;
      height: 4px;
      display: block;
    }
  }
  @include bp(phablet) {
    .about:before {
      left: -13px;
      content: "";
      width: 4px;
      height: 30px;
      background-color: white;
      display: block;
      position: absolute;
    }
  }
}
</style>