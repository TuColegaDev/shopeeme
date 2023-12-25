<template>
    
    <ul v-if="itemList.length > 0" role="list" class="divide-y divide-gray-200">
      <li v-for="item in itemList" :key="item.id" class="flex items-center justify-between rounded gap-x-6 bg-gray">
        <div class="flex flex-row items-center w-full px-5 py-3 hover:cursor-pointer"  @click="markItemAsDone(item.id)" >
            <button class="w-6 h-6 mr-5 bg-white rounded-3xl">
                <CheckIcon v-if="item.done" class="w-6 text-gray-400"/>
            </button>
            <p :class="['text-xl font-semibold leading-6 text-gray-800', { 'line-through text-gray-400': item.done } ]">{{ item.name }}</p>
        </div>
        <button class="px-5" @click="deleteListItem(item.id)">
            <XMarkIcon class="w-6 text-red-600"/>
        </button>
      </li>
    </ul>
    <div v-else class="m-10 text-center">
        <p class="text-xl text-gray-400">
            No hay productos que comprar.
        </p> 
    </div>
    <div class="flex items-center justify-center gap-12 mt-10 mb-5">
        <button class="inline-flex items-center px-4 py-2 text-sm font-bold text-white bg-blue-600 border border-blue-600 rounded hover:bg-white hover:text-blue-600">
            <PlusIcon class="w-5 mr-2"/>
            <span>Añadir</span>
        </button>
        <button @click="clearList()" class="inline-flex items-center px-4 py-2 text-sm font-bold text-white bg-gray-500 border border-gray-500 rounded hover:bg-white hover:text-gray-500">
            <ShoppingCartIcon class="w-5 mr-2"/>
            <span>Finalizar</span>
        </button>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import { PlusIcon, ShoppingCartIcon, XMarkIcon, CheckIcon } from "@heroicons/vue/16/solid"

  const markItemAsDone = (itemId) => {
    itemList.value.map(item => { if (item.id === itemId) { item.done = !item.done } })
  }

  const deleteListItem = (itemId) => {
    itemList.value = itemList.value.filter(item => item.id !== itemId)
  }

  const clearList = () => {
    itemList.value = []
  }

  const itemList = ref([
  {
        id: 1,
        name: 'Agua',
        done: false,
    },
    {
        id: 2,
        name: 'Pan',
        done: true,
    },
    {
        id: 3,
        name: 'Leche',
        done: false,
    },
    {
        id: 4,
        name: 'Huevos',
        done: false,
    },
    {
        id: 5,
        name: 'Ajos',
        done: false,
    },
    {
        id: 6,
        name: 'Cebollas',
        done: false,
    },
    
  ])
  </script>