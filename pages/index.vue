<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="12" md="12">
      <div class="Main-carousel">
        <Carousel :slides="slides" />
        <div class="log-in">
          <LogIn />
        </div>
      </div>

    </v-col>
  </v-row>
</template>

<script>
  export default {
    data() {
      return {
        slides: [{
            image: "/images/slide1.jpg"
          },
          {
            image: "/images/slide2.jpg"
          },
          {
            image: "/images/slide3.jpg"
          }
        ]
      }
    }

  }

</script>
<style scoped>
  .Main-carousel {
    height: 100vh;
    position: relative;
  }

  .log-in {
    position: absolute;
    top: 20%;
    right: 30px;
    width: 30%;
    height: 55%;
  }

</style>
