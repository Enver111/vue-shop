<script setup>
import CartList from "./components/CartList.vue";
import Drawer from "./components/Drawer.vue";
import Header from "./components/Header.vue";
</script>

<template>
  <!-- <Drawer /> -->
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14">
    <Header />
    <div class="p-10">
      <h2 class="text-3xl font-bold mb-8">Все товары</h2>
      <CartList />
    </div>
  </div>
</template>
