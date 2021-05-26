<template>
  <div class="nudes-wrapper">
    <div class="fixed-bar">
      <h2 class="headline-nudes">Nudes</h2>
      <div @click="onClickCircle" class="nav-circle"></div>
    </div>
    <div class="nudes-wrapper--content flex-grid">
      <div class="flex-row height-l">
        <div class="photo only-phablet"></div>
        <img class="photo" src="../assets/nd_009.jpg" alt="" srcset="" />
      </div>
      <div class="flex-row height-l">
        <img class="photo" src="../assets/nd_011.jpg" alt="" srcset="" />
        <img class="photo" src="../assets/nd_010.jpg" alt="" srcset="" />
      </div>

      <div class="section-gap"><hr></div>

      <div class="flex-row height-m">
        <img
          class="photo full-width"
          src="../assets/nd_004.jpg"
          alt=""
          srcset=""
        />
      </div>
      <div class="flex-row height-s">
        <img class="photo" src="../assets/nd_002.jpg" alt="" srcset="" />
        <img class="photo" src="../assets/nd_003.jpg" alt="" srcset="" />
      </div>

      <div class="flex-row height-l">
        <img
          class="photo full-width"
          src="../assets/nd_001.jpg"
          alt=""
          srcset=""
        />
      </div>

      <div class="section-gap"><hr></div>


      <div class="flex-row height-s">
        <img class="photo" src="../assets/nd_006.jpg" alt="" srcset="" />
        <img class="photo" src="../assets/nd_007.jpg" alt="" srcset="" />
      </div>

      <div class="flex-row height-l">
        <img
          class="photo full-width"
          src="../assets/nd_005.jpg"
          alt=""
          srcset=""
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Nudes",
  methods: {
    onClickCircle: function (e) {
      this.$emit("clickedCircle");
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../scss/breakpoints.scss";

.nudes-wrapper {
  min-height: 100vw;
  height: 100%;
  width: 100vw;
  background: black;

  .headline-nudes {
    margin: 0;
    padding: 15px 0;
    color: white;
    font-weight: 300;
  }

  .nav-circle {
    height: 15px;
    width: 15px;
    background-color: white;
    border-radius: 50%;
    position: absolute;
    top: 20px;
    right: 25px;
    cursor: pointer;
  }

  .fixed-bar {
    position: sticky;
    top: 0;
    background: black;
  }

  &--content {
    .photo {
      width: 100%;
      object-fit: cover;
      cursor: pointer;

      @include bp(tablet) {
        width: 45%;
        transition: all ease-in-out 1s;

        &:hover {
          transform: scale(1.1);
        }
      }
    }
  }
}
</style>