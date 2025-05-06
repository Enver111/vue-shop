<script setup>
import Cart from "./Cart.vue";

defineProps({
  items: Array,
});
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Cart
      v-for="item in items"
      :key="item.id"
      :image-url="item.imageUrl"
      :title="item.title"
      :price="item.price"
      :is-added="false"
      :isFavorite="false"
    />
  </div>
</template>
