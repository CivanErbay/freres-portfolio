<template>
  <div id="app">
    <div class="nav" :class="{ 'nav--active': navActive }">
      <a class="nudes">nudes</a>
      <a class="portraits">portraits</a>
      <a class="space">space</a>
      <a @click="changeComponent('About')" class="about">about</a>
      <button class="close-button" v-if="isMobile" @click="navActive = false">
        <div class="close-circle"></div>
      </button>
    </div>
    <component
      @clickedHeadline="navActive = true"
      @clickedBackdrop="navActive = false"
      :is="currentComponent"
    ></component>
  </div>
</template>

<script>
import Landing from "./views/Landing.vue";
import About from "./views/About.vue";

export default {
  name: "App",
  components: { Landing, About },
  data() {
    return {
      navActive: false,
      isMobile: false,
      currentComponent: 'Landing',
    };
  },
  methods: {
    changeComponent: function(compName) {
      this.currentComponent = compName;
      this.navActive = false;
    }
  },
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
  justify-content: flex-end;
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
    bottom: 35px;
    right: 20px;
    position: absolute;
  }

  .close-circle {
    width: 15px;
    height: 15px;
    border: solid white 3px;
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
    font-size: 24px;
    color: white;
    margin: 35px;
    text-decoration: none;
    cursor: pointer;

    @include bp(phablet) {
      font-size: 36px;
      margin: 0 35px;
    }

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
    width: 4px;
    height: 40px;
    background-color: white;
    display: inline-block;
    position: relative;
    left: -77px;

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
    width: 4px;
    height: 30px;
    background-color: white;
    display: inline-block;
    position: relative;
    left: -103px;

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
    width: 4px;
    height: 20px;
    background-color: white;
    display: inline-block;
    position: relative;
    left: -74px;

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