<script setup>
import Cart from "./Cart.vue";
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Cart
      image-url="/sneakers/sneakers-1.jpg"
      title="Мужские Кроссовки Nike Blazer Mid Suede"
      :price="5000"
      :is-added="true"
      :isFavorite="true"
    />
  </div>
</template>
