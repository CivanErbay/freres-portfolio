<template>
  <div class="nudes-wrapper">
    <div class="fixed-bar">
      <h2 class="headline-nudes">Nudes</h2>
      <div @click="onClickCircle" class="nav-circle"></div>
    </div>
    <div class="nudes-wrapper--content">
      <div class="carousel">
        <div class="carousel-cell">
          <img
            src="../assets/nd_001.jpg"
            alt="nudes one"
          />
        </div>
        <div class="carousel-cell">
           <img
            src="../assets/nd_002.jpg"
            alt="nudes one"
          />
        </div>
        <div class="carousel-cell">
          <img
            src="../assets/nd_003.jpg"
            alt="nudes one"
          />
        </div>
        <div class="carousel-cell">
           <img
            src="../assets/nd_004.jpg"
            alt="nudes one"
          />
        </div>
        <div class="carousel-cell">
          <img
            src="../assets/nd_005.jpg"
            alt="nudes one"
          />
        </div>
        <div class="carousel-cell">
          <img
            src="../assets/nd_006.jpg"
            alt="nudes one"
          />
        </div>
        <div class="carousel-cell">
           <img
            src="../assets/nd_007.jpg"
            alt="nudes one"
          />
        </div>
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
  mounted() {
    var carousel = document.querySelector(".carousel");
    var flkty = new Flickity(carousel, {
      imagesLoaded: true,
      percentPosition: false,
      wrapAround: true
    });

    var imgs = carousel.querySelectorAll(".carousel-cell img");
    // get transform property
    var docStyle = document.documentElement.style;
    var transformProp =
      typeof docStyle.transform == "string" ? "transform" : "WebkitTransform";

    flkty.on("scroll", function () {
      flkty.slides.forEach(function (slide, i) {
        var img = imgs[i];
        var x = ((slide.target + flkty.x) * -1) / 3;
        img.style[transformProp] = "translateX(" + x + "px)";
      });
    });
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
    * {
      box-sizing: border-box;
    }

    .carousel {
      background: #eee;
    }

    .carousel-cell {
      margin-right: 20px;
      overflow: hidden;
    }

    .carousel-cell img {
      display: block;
      height: 200px;
    }

    @media screen and (min-width: 768px) {
      .carousel-cell img {
        height: 400px;
      }
    }
    /*  .photo {
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
    } */
  }
}
</style>