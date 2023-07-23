<template>
  <section>
    <h1 class="text-center text-5xl my-5">Image carousel</h1>
    <div class="image-carousel">
      <div class="carousel-wrapper">
        <div
          v-if="images.length > 0"
          class="carousel-content"
          :style="{ transform: `translateX(-${currentIndex * 100}%)` }"
        >
          <div v-for="(image, index) in images" :key="index" class="carousel-item">
            <img :src="image" alt="Carousel Image" />
          </div>
        </div>
      </div>

      <div class="navigation-buttons">
        <button @click="prevSlide" :disabled="currentIndex === 0">Prev</button>
        <button @click="nextSlide" :disabled="currentIndex === images.length - 1">
          Next
        </button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";

const images = ref([
  "https://images.unsplash.com/photo-1502481851512-e9e2529bfbf9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1469&q=80",
  "https://images.unsplash.com/photo-1518972458649-b0f242a400ff?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80",
  "https://images.unsplash.com/photo-1456418047667-56bcd35b1a88?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80",
  "https://images.unsplash.com/photo-1554941426-e9604e34bc94?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80",
  // Add more image URLs as needed
]);

const currentIndex = ref(0);

const nextSlide = () => {
  if (currentIndex.value < images.value.length - 1) {
    currentIndex.value++;
  }
};

const prevSlide = () => {
  if (currentIndex.value > 0) {
    currentIndex.value--;
  }
};
</script>

<style scoped>
/* h1 {
  text-align: center;
} */
.image-carousel {
  max-width: 600px;
  margin: 0 auto;
  position: relative;
}

.carousel-wrapper {
  overflow: hidden;
}

.carousel-content {
  display: flex;
  transition: transform 0.3s ease;
}

.carousel-item {
  flex: 0 0 100%;
}

img {
  width: 100%;
  height: auto;
}

.navigation-buttons {
  display: flex;
  justify-content: space-between;
  position: absolute;
  top: 50%;
  left: 0;
  right: 0;
  transform: translateY(-50%);
}

button {
  background: rgba(0, 0, 0, 0.5);
  color: white;
  border: none;
  padding: 8px 12px;
  cursor: pointer;
}

button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.navigation-buttons button:first-child {
  border-radius: 5px 0 0 5px;
}

.navigation-buttons button:last-child {
  border-radius: 0 5px 5px 0;
}
</style>
