<template>
    <div class="p-2 mb-2 border-b border-gray-200 h-14">
        <div class="flex items-center justify-between">
            <input
                class="p-2 leading-tight text-gray-700 bg-transparent border-none appearance-none basis-5/6 shrink focus:outline-none"
                type="text" placeholder="Nuevo producto" v-model="itemName">
            <button @click="addNewItem"
                class="flex flex-row gap-2 p-1 text-sm text-black border-4 border-transparent rounded hover:text-blue-500">
                <PlusIcon class="w-5" />
                <span>
                    Añadir
                </span>
            </button>
        </div>
    </div>
</template>
<script setup>
import { defineEmits, ref } from 'vue'
import { PlusIcon } from '@heroicons/vue/16/solid'

const itemName = ref('')

const emit = defineEmits(['addItem'])

const addNewItem = () => {
    emit('addItem', itemName.value)
    itemName.value = ''
}
</script>