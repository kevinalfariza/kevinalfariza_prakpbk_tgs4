<template>
  <div :style="{ backgroundImage: `url(${selectedCake ? selectedCake.imageUrl : defaultBackground})` }" class="cake-container">
    <h1>Our Cakes</h1>
    <CakeList :cakes="cakes" @selectCake="handleSelectCake" />
    <div v-if="selectedCake" class="selected-cake">
      <h2>Selected Cake</h2>
      <p>Name: {{ selectedCake.name }}</p>
      <p>Price: {{ selectedCake.price }}</p>
    </div>
    <div v-if="!selectedCake" id="thank-you">
      <p>Thank you for visiting our cake shop!</p>
    </div>
    <slot></slot>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import CakeList from './CakeList.vue';

const cakes = ref([
  { id: 1, name: 'Strawberry Cake', price: '$10', imageUrl: 'https://asset.kompas.com/crops/jxp3roQFagBr5TlW8zUWRKk2vjY=/64x33:944x619/750x500/data/photo/2021/12/21/61c19b4956775.jpg' },
  { id: 2, name: 'Chocolate Cake', price: '$8', imageUrl:'https://t-2.tstatic.net/jogja/foto/bank/images/Resep-Kue-Cokelat-Ferrero-Rocher-ala-Rumahan-x12.jpg' },
  { id: 3, name: 'Vanilla Cake', price: '$9', imageUrl:'https://assets.promediateknologi.id/crop/0x0:0x0/750x500/webp/photo/p1/649/2023/10/10/resep-kue-sus-1940025970.jpg' }
]);

const selectedCake = ref(null);

const defaultBackground = 'https://example.com/path/to/default-background.jpg'; // Path ke gambar latar default

const handleSelectCake = (cake) => {
  selectedCake.value = cake;
};
</script>

<style scoped>
.cake-container {
  background-size: cover;
  background-position: center;
  min-height: 100vh;
  padding-bottom: 20px; /* Untuk memberikan ruang untuk konten di bagian bawah */
  transition: background-image 0.3s ease-in-out;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

.selected-cake {
  margin-top: 20px;
  border: 1px solid #ccc;
  padding: 10px;
  text-align: center;
  max-width: 300px;
  margin-left: auto;
  margin-right: auto;
  background-color: #fff; /* Background untuk kotak yang menunjukkan kue terpilih */
}

.selected-cake h2 {
  margin-top: 0;
}

.selected-cake p {
  margin: 5px 0;
}

#thank-you {
  margin-top: 20px;
  font-style: italic;
  color: #888;
}
</style>
