<script setup>
import Cart from "./components/Cart.vue";
import Header from "./components/Header.vue";
</script>

<template>
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14">
    <Header />
    <h2 class="text-3xl font-bold">Все товары</h2>

    <div>
      <Cart />
    </div>
  </div>
</template>
