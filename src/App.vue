<template>
  <div id="app">

      <div class="title">&nbsp;</div>

      <flickity ref="flickity" :options="flickityOptions">
        <div class="carousel-cell"><img alt="" src="./assets/jer_japan_01.jpg"></div>
        <div class="carousel-cell"><img alt="" src="./assets/jer_japan_02.jpg"></div>
        <div class="carousel-cell"><img alt="" src="./assets/jer_japan_03.jpg"></div>
        <div class="carousel-cell"><img alt="" src="./assets/jer_japan_04.jpg"></div>
        <div class="carousel-cell"><img alt="" src="./assets/jer_japan_05.jpg"></div>
      </flickity>

      <div class="info">

        <span class="">{{ artist }}</span>

        <span class="controls">
          <svg @click="previous()" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 11.7 19.8" style="enable-background:new 0 0 11.7 19.8;" xml:space="preserve">
          <path d="M11.7,1.8L9.9,0L0,9.9l9.9,9.9l1.8-1.8L3.5,9.9C3.5,9.9,11.7,1.8,11.7,1.8z"/>
          </svg>

          <span>1 / 5</span>

          <svg @click="next()" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 11.7 19.8" style="enable-background:new 0 0 11.7 19.8;" xml:space="preserve">
          <path d="M0,18l1.8,1.8l9.9-9.9L1.8,0L0,1.8l8.1,8.1C8.1,9.9,0,18,0,18z"/>
          </svg>
        </span>

        <span class="next-proj">Next Project</span>

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
      artist: 'Josh Epstein-Richards'
    }
  },
  methods: {
    next() {
      this.$refs.flickity.next();
    },
    
    previous() {
      this.$refs.flickity.previous();
    }
  }
}
</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  position: absolute;
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.carousel-cell {
  height: 70vh;
  width: 100%;
}

.carousel-cell img {
  display: block;
  max-height: 100%;
  max-width: 100%;
  margin: 0 auto;
}

.title,
.info {
  padding: 1rem;
}

.info,
.controls {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.controls svg {
  height: 20px;
  margin: 0 1rem;
  cursor: pointer;
}

</style>
