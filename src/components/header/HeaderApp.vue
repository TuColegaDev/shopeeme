<template>
  <header class="bg-white border-b">
    <nav class="flex items-center justify-between p-6 mx-auto max-w-7xl" aria-label="Global">
      <div class="flex lg:flex-1">
        <a href="" class="-m-1.5 p-1.5 flex items-center">
          <h2 class="text-3xl font-bold tracking-tight text-gray-900 truncate">ShopeeMe</h2>
        </a>
      </div>
      <div class="flex lg:hidden">
        <button type="button" class="-m-2.5 inline-flex items-center justify-center rounded-md p-2.5 text-gray-700" @click="mobileMenuOpen = true">
          <span class="sr-only">Open main menu</span>
          <Bars3Icon class="w-6 h-6" aria-hidden="true" />
        </button>
      </div>
      <div class="hidden sm:justify-end sm:flex">
        <ul class="flex gap-12">
          <li v-for="item in navigation" :key="item.id">
            <a :href="item.href" class="text-sm font-semibold leading-6 text-gray-900">{{ item.name }}</a>
          </li>
        </ul>
      </div>
    </nav>
    <div :class="['lg:hidden', { hidden: !mobileMenuOpen }]" @close="mobileMenuOpen = false">
      <div class="fixed inset-0 z-10" />
      <div class="fixed inset-y-0 right-0 z-10 w-full px-6 py-6 overflow-y-auto bg-white sm:max-w-sm sm:ring-1 sm:ring-gray-900/10">
        <div class="flex items-center justify-between">
          <a href="#" class="-m-1.5 p-1.5">
            <img width="42" height="42" src="@/assets/logo.png" />
          </a>
          <button type="button" class="-m-2.5 rounded-md p-2.5 text-gray-700" @click="mobileMenuOpen = false">
            <span class="sr-only">Close menu</span>
            <XMarkIcon class="w-6 h-6" aria-hidden="true" />
          </button>
        </div>
        <div class="flow-root mt-6">
          <div class="-my-6 divide-y divide-gray-500/10">
            <ul class="py-6 space-y-2">
              <li v-for="item in navigation" :key="item.id">
                <a :href="item.href" class="block px-3 py-2 -mx-3 text-base font-semibold leading-7 text-gray-900 rounded-lg hover:bg-gray-50">{{ item.name }}</a>
              </li>
            </ul>
            <div class="py-6">
              <a href="#" class="-mx-3 block rounded-lg px-3 py-2.5 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50">Log in</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue'

import {
  XMarkIcon,
  Bars3Icon
} from '@heroicons/vue/24/outline'

const mobileMenuOpen = ref(false)

const navigation = [
  {
    id: 1,
    name: 'Listas',
    href: '/',
    current: true,
  },
  {
    id: 2,
    name: 'Grupos',
    href: '/',
    current: false,
  },
  {
    id: 3,
    name: 'Perfil',
    href: '/',
    current: false,
  }
]
</script>