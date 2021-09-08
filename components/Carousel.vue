<template>
  <div class="slider">
    <transition tag="div" name="fade" >
      <div v-if="show" :key="current" class="slide">
        <img :src="slides[current].image" width="100%" height="100%">
      </div>
    </transition>
    <div class="carousel__controls">
      <ul class="carousel__dots-container">
        <li v-for="(dot,i) in cDots" :key="i" :class="{'carousel__dot': true, 'carousel__dot_active': dot===current}">
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      slides: {
        type: Array,
        default: []
      }
    },
    data() {
      return {
        current: 0,
        transitionName: "fade",
        Interval: '',
        show: false,
        prev: false,

      }

    },
    computed: {
      cDots: function () {
        return Array(this.slides.length).fill().map(
          function (_, i) {
            return i;
          }
        )
      }
    },
    methods: {
      goPrev: function () {
        this.prev = true;
        if (this.current === 0) {
          this.current = this.slides.length - 1;
        } else {
          this.current -= 1;
        }
      }
    },
   beforeMount () {
      this.show = true;
      this.Interval = setInterval(() => {
        this.goPrev();
      }, 8000);
    },
    beforeDestroy() {
      clearInterval(this.Interval)
    },
  }

</script>

<style scoped>
.fade-enter-active, .fade-leave-active {
  transition: opacity 2.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

  .slider {
    width: 100%;
    height: 100%;
    position: relative;
  }

  .slide {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  /* .btn {
    z-index: 10;
    cursor: pointer;
    border: 3px solid #fff;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 70px;
    height: 70px;
    position: absolute;
    top: calc(100% - 100px);
    left: 1%;
    transition: transform 0.3s ease-in-out;
    user-select: none;
  }

  .btn-prev {
    margin-left: 80px;
  }

  .btn:hover {
    transform: scale(1.1);
  } */

  /* /////////////////dots */
  .carousel__controls {
    display: flex;
    width: 100%;
    justify-content: center;
    align-items: center;
    width: 70px;
    height: 70px;
    position: absolute;
    top: calc(100% - 100px);
    left: 5%;
  }

  .carousel__dots-container {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
  }

  .carousel__dot {
    width: 3px;
    height: 3px;
    background-color: #90A4AE;
    border-radius: 100%;
    margin: 0 7px;
  }

  .carousel__dot_active {
    background-color: #ECEFF1;
    cursor: normal;
    width: 15px;
height: 1px;
    border-radius: 10px;
  }

</style>
