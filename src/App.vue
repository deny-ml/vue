<template>
  <div id="app">
    <div class="container">
      <!-- Click Counter -->
      <div class="click-counter">
        <h2>Click Counter</h2>
        <p>Click count: {{ clickCount }}</p>
        <button @click="incrementCounter">Click Me!</button>
      </div>

      <!-- Box Color Changer -->
      <div class="color-changer">
        <h2>Box Color Changer</h2>
        <div :style="{ backgroundColor: boxColor }" class="color-box"></div>
        <button @click="changeColor('red')">Red</button>
        <button @click="changeColor('blue')">Blue</button>
        <button @click="changeColor('green')">Green</button>
      </div>

      <!-- Image Carousel -->
      <div class="carousel">
        <h2>Image Carousel</h2>
        <vue-slick-carousel :options="carouselOptions">
          <div v-for="(image, index) in images" :key="index" class="carousel-slide">
            <img :src="image" alt="Carousel Image" class="carousel-image" />
          </div>
        </vue-slick-carousel>
      </div>
    </div>
  </div>
</template>

<script>
import VueSlickCarousel from 'vue-slick-carousel';
import 'vue-slick-carousel/dist/vue-slick-carousel.css';
import 'slick-carousel/slick/slick.css';
import 'slick-carousel/slick/slick-theme.css';

export default {
  name: 'App',
  components: {
    VueSlickCarousel
  },
  data() {
    return {
      clickCount: 0,
      boxColor: 'white',
      images: [
        'https://via.placeholder.com/400x200?text=Image+1',
        'https://via.placeholder.com/400x200?text=Image+2',
        'https://via.placeholder.com/400x200?text=Image+3'
      ],
      carouselOptions: {
        dots: true,
        arrows: true,
        infinite: true,
        speed: 500,
        slidesToShow: 1,
        slidesToScroll: 1
      }
    };
  },
  methods: {
    incrementCounter() {
      this.clickCount++;
    },
    changeColor(color) {
      this.boxColor = color;
    }
  }
};
</script>

<style scoped>
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

.click-counter,
.color-changer,
.carousel {
  margin-bottom: 40px;
}

.color-box {
  width: 100px;
  height: 100px;
  margin-bottom: 10px;
}

.carousel-slide {
  text-align: center;
}

.carousel-image {
  width: 100%;
  height: auto;
}
</style>
