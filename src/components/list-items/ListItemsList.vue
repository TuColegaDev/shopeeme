<template>
    <ul v-if="list.length > 0" role="list" class="divide-y divide-gray-500/10">
        <li v-for="item in list" :key="item.id" class="flex items-center justify-between rounded gap-x-6 bg-gray">
            <div class="flex flex-row items-center w-full px-5 py-3 hover:cursor-pointer" @click="markItemAsDone(item.id)">
                <button class="w-6 h-6 mr-5 bg-white rounded-3xl">
                    <CheckIcon v-if="item.done" class="w-6 text-gray-800" />
                </button>
                <p :class="['text-xl font-semibold leading-6 text-gray-800', { 'line-through text-gray-500/50': item.done }]">
                    {{ item.name }}</p>
            </div>
            <button class="px-5" @click="deleteListItem(item.id)">
                <XMarkIcon class="w-6 text-red-600" />
            </button>
        </li>
    </ul>
    <div v-else class="m-10 text-center">
        <p class="text-xl text-gray-400">
            No hay productos en la lista.
        </p>
    </div>
</template>
  
<script setup>
import { defineProps, defineEmits } from 'vue'
import { XMarkIcon, CheckIcon } from "@heroicons/vue/16/solid"

defineProps({
    list: Array
})

const emit = defineEmits(['deleteItem', 'buyItem'])

function markItemAsDone(itemId) {
    emit('buyItem', itemId)
}

function deleteListItem(itemId) {
    emit('deleteItem', itemId)
}
</script>