<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
  cake: Object
});

const emit = defineEmits(['selectCake']);

const selectCake = () => {
  emit('selectCake', props.cake);
};
</script>

<template>
  <div class="cake-item" @click="selectCake">
    <h3>{{ cake.name }}</h3>
    <p>{{ cake.price }}</p>
  </div>
</template>

<style scoped>
.cake-item {
  border: 1px solid #ccc;
  padding: 10px;
  margin: 5px;
  cursor: pointer;
}
</style>
<style scoped>
.cake-item {
  border: 1px solid #ccc;
  padding: 10px;
  margin: 5px;
  cursor: pointer;
  transition: transform 0.3s ease;
}

.cake-item:hover {
  transform: scale(1.05);
}

.cake-info {
  text-align: center;
}

.cake-name {
  font-size: 18px;
  margin-bottom: 5px;
}

.cake-price {
  font-size: 14px;
  color: #888;
}
</style>

