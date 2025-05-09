<script setup>
import { onMounted, provide, reactive, ref, watch } from "vue";
import axios from "axios";
import CartList from "./components/CartList.vue";
import Drawer from "./components/Drawer.vue";
import Header from "./components/Header.vue";

const items = ref([]);

const filters = reactive({
  sortBy: "title",
  searshQuery: "",
});

const onChangeSelect = (event) => {
  filters.sortBy = event.target.value;
};

const onChangeSearchInput = (event) => {
  filters.searshQuery = event.target.value;
};

const fetchFavorites = async () => {
  try {
    const { data: favorites } = await axios.get(
      `https://58419295808a7aa4.mokky.dev/favorites`
    );
    items.value = items.value.map((item) => {
      const favorite = favorites.find(
        (favorite) => favorite.productId === item.id
      );

      if (!favorite) {
        return item;
      }
      return {
        ...item,
        isFavorite: true,
        favoriteId: favorite.id,
      };
    });
  } catch (error) {
    console.log(error);
  }
};

const addToFavorite = async (item) => {
  try {
    const obj = {
      parentId: item.id,
    };
    const { data } = await axios.post(
      `https://58419295808a7aa4.mokky.dev/favorites`,
      obj
    );
    item.isFavorite = true;
  } catch (err) {
    console.log(err);
  }
};

const fetchItems = async () => {
  try {
    const params = {
      sortBy: filters.sortBy,
    };

    if (filters.searshQuery) {
      params.title = `*${filters.searshQuery}*`;
    }
    const { data } = await axios.get(
      `https://58419295808a7aa4.mokky.dev/items`,
      { params }
    );
    items.value = data.map((obj) => ({
      ...obj,
      isFavorite: false,
      isAdded: false,
    }));
  } catch (error) {
    console.log(error);
  }
};

onMounted(async () => {
  await fetchItems();
  await fetchFavorites();
});
watch(filters, fetchItems);

provide("addToFavorite", addToFavorite);
</script>

<template>
  <!-- <Drawer /> -->
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14">
    <Header />
    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все товары</h2>

        <div class="flex gap-4">
          <select
            @change="onChangeSelect"
            class="py-2 px-3 border border-gray-200 rounded-md outline-none"
            name=""
            id=""
          >
            <option value="name">По названию</option>
            <option value="price">По цене (дешевые)</option>
            <option value="-price">Дорогие</option>
          </select>
          <div class="relative">
            <img class="absolute left-4 top-3" src="/search.svg" alt="Search" />
            <input
              @input="onChangeSearchInput"
              class="border border-gray-200 rounded-md py-2 pl-11 pr-4 outline-none focus:border-gray-400 transition"
              placeholder="Поиск..."
              type="text"
            />
          </div>
        </div>
      </div>
      <div class="mt-10">
        <CartList :items="items" @addToFavorite="addToFavorite" />
      </div>
    </div>
  </div>
</template>
