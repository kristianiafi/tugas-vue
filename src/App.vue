<template>
  <div id="app">
    <!-- Click Counter -->
    <div class="counter">
      <h2>Click Counter</h2>
      <p>Count: {{ count }}</p>
      <button @click="incrementCount">Increment</button>
    </div>

    <!-- Box Color Changer -->
    <div class="box-color-changer">
      <h2>Box Color Changer</h2>
      <div :style="{ backgroundColor: boxColor }" class="color-box"></div>
      <button @click="changeColor">Change Color</button>
    </div>

    <!-- Image Carousel -->
    <div class="carousel">
      <h2>Image Carousel</h2>
      <img :src="images[currentImage]" class="carousel-image" />
      <button @click="prevImage">Previous</button>
      <button @click="nextImage">Next</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // Data untuk Click Counter
      count: 0,

      // Data untuk Box Color Changer
      boxColor: 'red',
      colors: ['red', 'blue', 'green', 'yellow', 'purple'],

      // Data untuk Image Carousel
      images: [
        'https://austin.culturemap.com/media-library/seventeen-k-pop-group.jpg?id=53120131&width=2000&height=1500&quality=65&coordinates=0%2C0%2C0%2C0',
        'https://intodaymedia.com/storage/articles/TE2NMh2BPGjk6d8IvLu0Y1HWzGBiDwCaGhVBWTnI.jpg',
        'https://asset.kompas.com/crops/4ijROuHkksioCOSitJuUULUOUvQ=/0x0:900x600/750x500/data/photo/2023/08/29/64ed58855f803.jpg'
      ],
      currentImage: 0
    }
  },
  methods: {
    // Method untuk Click Counter
    incrementCount() {
      this.count++
    },

    // Method untuk Box Color Changer
    changeColor() {
      const randomIndex = Math.floor(Math.random() * this.colors.length)
      this.boxColor = this.colors[randomIndex]
    },

    // Method untuk Image Carousel
    prevImage() {
      this.currentImage = this.currentImage === 0 ? this.images.length - 1 : this.currentImage - 1
    },
    nextImage() {
      this.currentImage = this.currentImage === this.images.length - 1 ? 0 : this.currentImage + 1
    }
  }
}
</script>

<style scoped>
#app {
  display: flex;
  flex-direction: column; /* Mengatur elemen agar ditampilkan vertikal */
  align-items: center; /* Untuk menyejajarkan konten di tengah */
  text-align: center;
}

.counter,
.box-color-changer,
.carousel {
  margin: 20px 0;
}

.color-box {
  width: 200px;
  height: 200px;
  margin: 20px 0;
}

.carousel-image {
  width: 300px;
  height: 200px;
  display: block;
  margin: 0 auto;
}

button {
  margin-top: 10px;
}
</style>
