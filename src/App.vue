<script setup>
import CakeShop from './components/CakeShop.vue';
</script>

<template>
  <div>
    <CakeShop>
      <template v-slot>
        <div>
          <p>Thank you for visiting our cake shop!</p>
        </div>
      </template>
    </CakeShop>
  </div>
</template>

<style scoped>
div {
  text-align: center;
}
</style>
<style scoped>
div {
  text-align: center;
  margin-top: 20px;
}
</style>

