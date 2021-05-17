<template>
  <div class="nudes-wrapper">
    <div class="fixed-bar">
      <h2 class="headline-nudes">Nudes</h2>
      <div @click="onClickCircle" class="nav-circle"></div>
    </div>
    <div class="nudes-wrapper--content flex-grid">
      <div class="flex-row">
        <div class="photo only-phablet"></div>
        <img class="photo photo-l" src="../assets/img2.jpeg" alt="" srcset="" />
      </div>
      <div class="flex-row">
        <img class="photo photo-l" src="../assets/img4.jpeg" alt="" srcset="" />
        <img class="photo photo-l" src="../assets/img3.jpeg" alt="" srcset="" />
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
      padding: 30px 0;
      height: 80vh;
      width: 100%;
      object-fit: contain;

      /*   &-l {
        height: 300px;
        width: 100%;
        object-fit: contain;
      }
      &-m {
        height: 200px;
        width: 100%;
        object-fit: contain;
      }
      &-s {
        height: 100px;
        width: 100%;
        object-fit: contain;
      } */
    }
  }
}
</style>