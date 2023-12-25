<template>
  <header class="bg-white border-b">
    <nav class="flex items-center justify-between p-6 mx-auto max-w-7xl" aria-label="Global">
      <div class="flex lg:flex-1">
        <a href="" class="-m-1.5 p-1.5 flex items-center">
          <!-- <img width="42" height="42" src="@/assets/logo.png"/> -->
          <h2 class="text-3xl font-bold tracking-tight text-gray-900 truncate">ShopeeMe</h2>
        </a>
      </div>
      <div class="flex lg:hidden">
        <button type="button" class="-m-2.5 inline-flex items-center justify-center rounded-md p-2.5 text-gray-700">
          <span class="sr-only">Open main menu</span>
          <Bars3Icon class="w-6 h-6" aria-hidden="true" />
        </button>
      </div>
    </nav>
  </header>
</template>

<script setup>
import {
  Bars3Icon,
} from '@heroicons/vue/24/outline'
</script>