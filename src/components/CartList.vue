<script setup>
import Cart from "./Cart.vue";

defineProps({
  items: Array,
  addToFavorite: Function,
});

const emit = defineEmits(["addToFavorite"]);
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Cart
      v-for="item in items"
      :key="item.id"
      :id="item.id"
      :image-url="item.imageUrl"
      :title="item.title"
      :price="item.price"
      :onClickFavorite="() => emit('addToFavorite', item)"
      :isFavorite="item.isFavorite"
    />
  </div>
</template>
