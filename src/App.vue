<template>
  <div id="app">
    <div class="nav" :class="{ 'nav--active': navActive }">
      <a class="nudes">nudes</a>
      <a class="portraits">portraits</a>
      <a class="space">space</a>
      <a class="about">about</a>
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
    };
  },
  methods: {},
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;700&display=swap");

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
  transform: translateY(-700px);
  position: absolute;
  transition: ease-out 0.9s;
  width: 100%;
  height: 450px;
  z-index: 2;
  background-color: black;
  display: flex;
  justify-content: flex-start;
  align-items: center;

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
      margin-left: 150px;
    }

    &.about {
      right: 30px;
      top: 50px;
      font-size: 30px;
      position: absolute;
    }
  }

  .nudes:after {
    content: "";
    width: 80px;
    height: 4px;
    background-color: white;
    display: block;
    position: relative;
    bottom: -40px;
  }
  .portraits:after {
    content: "";
    width: 70px;
    height: 4px;
    background-color: white;
    display: block;
    position: relative;
    bottom: -20px;
  }
  .space:after {
    content: "";
    width: 50px;
    height: 4px;
    background-color: white;
    display: block;
    position: relative;
    bottom: -5px;
  }

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
</style>