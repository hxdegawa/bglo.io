<template lang="pug">
  .carousel-wrapper(@mousemove="updatePosition($event)")
    carousel.carousel(:navigationEnabled="true" :autoplay="false" adjustableHeightEasing="false" :loop="true" :perPage="1" :paginationEnabled="false" :adjustableHeight="false")

      slide.slide.slide1
        img(src="~assets/mask-base/mask-1.jpeg" v-bind:style="{'mask-position': `${parallaxCoordinates.slide1.maskX}px ${parallaxCoordinates.slide1.maskY}px`}").part-B
        span(v-bind:style="{'transform': `translate(calc(-50% - ${parallaxCoordinates.slide1.textX}px), calc(-50% - ${parallaxCoordinates.slide1.textY}px))`}") beloved.

      slide.slide.slide2
        img(src="~assets/mask-base/mask-2.jpeg" v-bind:style="{'mask-position': `${parallaxCoordinates.slide2.maskX}px ${parallaxCoordinates.slide2.maskY}px`}").part-G
        span(v-bind:style="{'transform': `translate(calc(-50% - ${parallaxCoordinates.slide2.textX}px), calc(-50% - ${parallaxCoordinates.slide2.textY}px))`}") genuine.

      slide.slide.slide3
        img(src="~assets/mask-base/mask-3.jpeg" v-bind:style="{'mask-position': `${parallaxCoordinates.slide3.maskX}px ${parallaxCoordinates.slide3.maskY}px`}").part-L
        span(v-bind:style="{'transform': `translate(calc(-50% - ${parallaxCoordinates.slide3.textX}px), calc(-50% - ${parallaxCoordinates.slide3.textY}px))`}") logical.

      slide.slide.slide4
        img(src="~assets/mask-base/mask-4.jpeg" v-bind:style="{'mask-position': `${parallaxCoordinates.slide4.maskX}px ${parallaxCoordinates.slide4.maskY}px`}").part-O
        span(v-bind:style="{'transform': `translate(calc(-50% - ${parallaxCoordinates.slide4.textX}px), calc(-50% - ${parallaxCoordinates.slide4.textY}px))`}") outrageous.
</template>

<script>
export default {
  data() {
    return {
      parallaxCoordinates: {
        slide1: {
          maskX: 100,
          maskY: 80,
          textX: 0,
          textY: 0,
        },
        slide2: {
          maskX: 100,
          maskY: 80,
          textX: 0,
          textY: 0,
        },
        slide3: {
          maskX: 100,
          maskY: 80,
          textX: 0,
          textY: 0,
        },
        slide4: {
          maskX: 100,
          maskY: 80,
          textX: 0,
          textY: 0,
        },
      },
      activeElementClass: null
    }
  },
  methods: {
    updatePosition(e) {
      this.$nextTick(function() {
        const selectedSlide = this.$el.querySelector('.VueCarousel-slide-active');
        const match = selectedSlide ? selectedSlide.className.match(/slide[0-9]/)[0] : this.$el.getElementsByClassName("slide1")[0].className.match(/slide[0-9]/)[0];

        this.parallaxCoordinates[match].maskX = (Math.floor(e.clientX + 80 - this.$el.offsetWidth / 2) / 30) + 100;
        this.parallaxCoordinates[match].maskY = (Math.floor(e.clientY - 20 - this.$el.offsetHeight / 2) / 30) + 80;

        this.parallaxCoordinates[match].textX = (Math.floor(e.clientX - this.$el.offsetWidth / 2) / 50);
        this.parallaxCoordinates[match].textY = (Math.floor(e.clientY - this.$el.offsetHeight / 2) / 50);
      })
    },
  },
  computed: {
  }
};
</script>

<style lang="scss">
.carousel-wrapper {
  position: absolute;
  height: 100%;
  width: 100%;

  * {
    outline: none !important;
  }

  .carousel {
    position: relative;
    margin: 0 auto;
    max-width: 80vw;
    top: 20%;
    height: 60%;

    .VueCarousel-wrapper {
      position: absolute;
      height: 100%;
      width: 100%;

      .VueCarousel-inner {
        position: absolute;
        height: 100% !important;
        width: 100%;
      }
    }

    .carousel__list {
      position: absolute;
      width: 100%;
      height: 100%;

      .carousel__item {
        position: absolute;
        height: 100%;
        width: 100%;
      }
    }

    .slide {
      position: relative;
      width: 100%;

      span {
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50% , -50%);
        font-size: 70px;
        font-weight: 700;
        letter-spacing: 3px;
        text-transform: uppercase;
      }
    }

    [class*="part-"] {
      position: absolute;
      height: 400px;
      width: 400px;
      left: calc(50% - 200px);
      top: calc(50% - 200px);
      filter: grayscale(1);
      object-fit: cover;
      mask-mode: alpha;
      mask-repeat: no-repeat;
      mask-position: center;
      mask-size: 240px;
      mask-origin: stroke-box;

      &.part-B {
        mask-image: url('~assets/mask-image/bglo-b.svg');
      }

      &.part-G {
        mask-image: url('~assets/mask-image/bglo-g.svg');
      }

      &.part-L {
        mask-image: url('~assets/mask-image/bglo-l.svg');
      }

      &.part-O {
        mask-image: url('~assets/mask-image/bglo-o.svg');
      }
    }
  }
}
</style>
