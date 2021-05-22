<template>
  <div id="app">
    <div class="nav" :class="{ 'nav--active': navActive }">
      <a
        @click="changeComponent('Nudes')"
        class="nudes"
        :class="{ 'nudes--active': currentComponent == 'Nudes' }"
        >nudes</a
      >
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
      @clickedCircle="navActive = true"
      :is="currentComponent"
    ></component>
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
import Landing from "./views/Landing.vue";
import About from "./views/About.vue";
import Nudes from "./views/Nudes.vue";

export default {
  name: "App",
  components: { Landing, About, Nudes },
  data() {
    return {
      navActive: false,
      showBackdrop: false,
      isMobile: false,
      currentComponent: "Landing",
    };
  },
  methods: {
    changeComponent: function (compName) {
      this.currentComponent = compName;
      this.navActive = false;
    },
    onClickBackdrop: function (e) {
      this.navActive = false;
      this.showBackdrop = false;
    },
  },
  watch: {
    navActive: function () {
      this.navActive ? (this.showBackdrop = true) : (this.showBackdrop = false);
    },
    showBackdrop: function () {
      if (this.isMobile) this.showBackdrop = false;
    },
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

  .flex-grid {
    display: flex;
    flex-direction: column;
    align-items: center;

    .flex-row {
      display: flex;
      flex-direction: column;

      @include bp(phablet) {
        flex-direction: row;
        justify-content: space-around;
        width: 100%;
      }
    }
  }

  .only-phablet {
    display: none;

    @include bp(phablet) {
      display: block;
    }
  }

  .full-width {
    width: 100%;
  }
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
    height: 390px;
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

  .nudes {
    /*  &--active {
      :after {
      UPCOMING TODO
        }
      }
    } */

    &:after {
      content: "";
      width: 4px;
      height: 40px;
      background-color: white;
      display: inline-block;
      position: relative;
      left: -77px;

      @include bp(phablet) {
        width: 70px;
        height: 4px;
        display: block;
        bottom: -5px;
        left: unset;
        transition: bottom 0.3s ease-in;
      }
    }
    &:hover {
      &:after {
        @include bp(phablet) {
          bottom: -20px;
        }
      }
    }
  }
  .portraits {
    &:after {
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
        bottom: -5px;
        left: unset;
        transition: bottom 0.3s ease-in;
      }
    }

    &:hover {
      &:after {
        @include bp(phablet) {
          bottom: -20px;
        }
      }
    }
  }
  .space {
    &:after {
      content: "";
      width: 4px;
      height: 20px;
      background-color: white;
      display: inline-block;
      position: relative;
      left: -74px;

      @include bp(phablet) {
        width: 70px;
        height: 4px;
        display: block;
        bottom: -5px;
        left: unset;
        transition: bottom 0.3s ease-in;
      }
    }
    &:hover {
      &:after {
        @include bp(phablet) {
          bottom: -20px;
        }
      }
    }
  }

  .about {
    @include bp(phablet) {
      &:before {
        left: -10px;
        content: "";
        width: 4px;
        height: 30px;
        background-color: white;
        display: block;
        position: absolute;
        transition: left 0.3s ease-in;
      }
    }

    &:hover {
      &:before {
        @include bp(phablet) {
          left: -20px;
        }
      }
    }
  }
}

.backdrop {
  width: 100vw;
  height: 100vh;
  z-index: 1;
  background-color: rgba($color: #000000, $alpha: 0.8);
  transition: opacity 0.4s ease-in-out;
  position: absolute;
  cursor: pointer;
  top: 0;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.4s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0.4;
}
</style>