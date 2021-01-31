<template>
  <div id="app">

      <div class="carousel">
        <flickity ref="flickity" :options="flickityOptions">
          <div class="carousel-cell">
            <div class="carousel-image">
              <img alt="" :src="imageOne">
            </div>
          </div>
          <div class="carousel-cell">
            <div class="carousel-image">
              <img alt="" :src="imageTwo">
            </div>
            </div>
          <div class="carousel-cell">
            <div class="carousel-image">
              <img alt="" :src="imageThree">
            </div>
            </div>
          <div class="carousel-cell">
            <div class="carousel-image">
              <img alt="" :src="imageFour">
            </div>
            </div>
          <div class="carousel-cell">
            <div class="carousel-image">
              <img alt="" :src="imageFive">
            </div>
            </div>
        </flickity>
      </div>

      <div class="info">

        <span>{{ artist }}</span>

        <span class="controls">
          <svg @click="previous()" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 11.7 19.8" style="enable-background:new 0 0 11.7 19.8;" xml:space="preserve">
          <path d="M11.7,1.8L9.9,0L0,9.9l9.9,9.9l1.8-1.8L3.5,9.9C3.5,9.9,11.7,1.8,11.7,1.8z"/>
          </svg>
          <svg @click="next()" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 11.7 19.8" style="enable-background:new 0 0 11.7 19.8;" xml:space="preserve">
          <path d="M0,18l1.8,1.8l9.9-9.9L1.8,0L0,1.8l8.1,8.1C8.1,9.9,0,18,0,18z"/>
          </svg>
        </span>

        <span v-on:click="nextProj" class="next-proj">Next Project</span>

      </div>

  </div>
</template>

<script>
import Flickity from 'vue-flickity';

export default {
  name: 'App',
  components: {
    Flickity
  },
  data() {
    return {
      flickityOptions: {
        initialIndex: 2,
        prevNextButtons: false,
        pageDots: false,
        wrapAround: true
      },
      artist: 'Josh Epstein-Richards',
      imageOne: require('./assets/jer_japan_01.jpg'),
      imageTwo: require('./assets/jer_japan_02.jpg'),
      imageThree: require('./assets/jer_japan_03.jpg'),
      imageFour: require('./assets/jer_japan_04.jpg'),
      imageFive: require('./assets/jer_japan_05.jpg')
    }
  },
  methods: {
    next() {
      this.$refs.flickity.next();
    },
    previous() {
      this.$refs.flickity.previous();
    }
    ,
    nextProj() {
      this.artist = 'Sammy Taylor',
      this.imageOne = require('./assets/st_japan_01.jpg'),
      this.imageTwo = require('./assets/st_japan_02.jpg'),
      this.imageThree = require('./assets/st_japan_03.jpg'),
      this.imageFour = require('./assets/st_japan_04.jpg'),
      this.imageFive = require('./assets/st_japan_05.jpg')
    }
  }
}

// 100vh on mobile
let vh = window.innerHeight * 0.01;
document.documentElement.style.setProperty('--vh', `${vh}px`);
</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  height: 100vh;
  height: calc(var(--vh, 1vh) * 100);
  width: 100%;
}

.carousel {
  top: 4.5rem;
  position: absolute;
  width: 100%;
}

.carousel .carousel-cell,
.carousel .flickity-enabled,
.carousel .flickity-viewport{
  height: calc(100vh - 9rem);
}

.carousel-cell {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.carousel-image {
  display: flex;
  width: 100%;
  height: 100%;
}

.carousel-cell img {
  object-fit: contain;
  border: none;
  width: 100%;
  height: 100%;
  max-width: 100%;
  max-height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}

.info,
.controls {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.info {
  position: fixed;
  bottom: 0;
  width: 100%;
}

.info span {
  padding: 1rem;
}

.controls {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
}

.controls svg {
  height: 20px;
  margin: 0 1rem;
  cursor: pointer;
  fill: #2c3e50;
}

.next-proj {
  cursor: pointer;
}

@media screen and (max-width: 480px) {

  .controls {
    display: none;
  }

  .carousel {
    top: 3rem;
  }

}

</style>
