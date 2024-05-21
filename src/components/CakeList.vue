<template>
    <div>
      <ul>
        <li v-for="cake in cakes" :key="cake.id">
          <img :src="cake.imageUrl" :alt="cake.name" @click="selectCake(cake)" />
          <button 
            :class="{
              'strawberry-btn': cake.name.includes('Strawberry') && selectedCakeId === cake.id,
              'chocolate-btn': cake.name.includes('Chocolate') && selectedCakeId === cake.id,
              'vanilla-btn': cake.name.includes('Vanilla') && selectedCakeId === cake.id
            }"
            @click="selectCake(cake)">
            Select
          </button>
        </li>
      </ul>
    </div>
  </template>
  
  <script setup>
  const props = defineProps({
    cakes: Array,
    selectedCakeId: Number
  });
  
  const emit = defineEmits(['selectCake']);
  
  const selectCake = (cake) => {
    emit('selectCake', cake);
  };
  </script>
  
  <style scoped>
  ul {
    list-style: none;
    padding: 0;
  }
  
  li {
    margin-bottom: 20px;
    text-align: center;
  }
  
  img {
    max-width: 100px;
    cursor: pointer;
  }
  
  button {
    padding: 5px 10px; 
    border: none;
    cursor: pointer;
    margin-top: 10px;
    font-size: 0.8em; 
    border-radius: 5px; 
    transition: background-color 0.3s;
  }
  
  button:hover {
    opacity: 0.8; 
  }
  
  .strawberry-btn {
    background-color: rgba(255, 0, 0, 0.7); 
  }
  
  .chocolate-btn {
    background-color: rgba(139, 69, 19, 0.7); 
  }
  
  .vanilla-btn {
    background-color: rgba(255, 228, 196, 0.7); 
  }
  </style>
  