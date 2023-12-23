<template>
  <div id="app">
    <div class="image-container">
      <img :src="imgUrl" class="cat-image" />
    </div>
    <div class="button-container">
      <button @click="getCat" class="update-button">Обновить фотографию</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      imgUrl: ''
    }
  },
  methods: {
    getCat() {
      fetch('https://api.thecatapi.com/v1/images/search')
        .then(response => response.json())
        .then(data => {
          this.imgUrl = data[0].url;
        })
    }
  },
  mounted() {
    this.getCat();
  }
}
</script>

<style scoped>
#app {
  text-align: center;
  padding: 20px;
}

.image-container {
  width: 80%;
  margin: 0 auto;
}

.cat-image {
  max-width: 100%;
  height: auto;
  margin-bottom: 20px;
}

.button-container {
  display: flex;
  justify-content: center;
  margin-top: 20px;
}

.update-button {
  padding: 5px 10px; /* Smaller size */
  font-size: 16px; /* Smaller font */
  background-color: #39ff14; /* Neon green */
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.update-button:hover {
  background-color: #2fba0f; /* Darker neon green */
}
</style>
