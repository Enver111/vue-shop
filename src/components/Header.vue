<template>
  <header class="flex justify-between border-b border-slate-300 px-10 py-8">
    <div class="flex items-center gap-4">
      <img src="/logo.png" alt="Logo" class="w-10" />
      <div>
        <h2 class="text-xl font-bold uppercase">Vue Shop</h2>
        <p class="text-slate-400">Магазин лучших кроссовок</p>
      </div>
    </div>

    <ul class="flex items-center gap-10">
      <li
        class="flex items-center gap-3 text-gray-400 hover:text-black cursor-pointer"
      >
        <img src="/cart.svg" alt="Cart" />
        <b>1205 руб.</b>
      </li>
      <li
        class="flex items-center gap-3 text-gray-400 hover:text-black cursor-pointer"
      >
        <img src="/heart.svg" alt="Heart" />
        <span>Закладки</span>
      </li>
      <li
        class="flex items-center gap-3 text-gray-400 hover:text-black cursor-pointer"
      >
        <img src="/profile.svg" alt="Profile" />
        <span>Профиль</span>
      </li>
    </ul>
  </header>
</template>
