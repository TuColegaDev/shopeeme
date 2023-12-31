<template>
    <div class="flex flex-row items-center justify-center gap-6 mt-10 mb-5 sm:flex-row sm:gap-12">
        <button class="inline-flex items-center px-4 py-2 text-xs font-bold text-white bg-blue-600 border border-blue-600 rounded hover:bg-white hover:text-blue-600">
            <PlusIcon class="w-6 mr-2"/>
            <span>Añadir</span>
        </button>
        <button @click="openClearListModal" class="inline-flex items-center px-4 py-2 text-xs font-bold text-white bg-gray-600 border border-gray-600 rounded hover:bg-white hover:text-gray-600">
            <ShoppingCartIcon class="w-6 mr-2"/>
            <span class="text-xl[20px] sm:text-sm">Finalizar</span>
        </button>
    </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'
import { PlusIcon } from "@heroicons/vue/16/solid"
import { ShoppingCartIcon } from '@heroicons/vue/24/outline';

defineProps({
    disabled: Boolean
})

const emit = defineEmits(['openClearListModal'])

const openClearListModal = () => {
    emit('openClearListModal')
}
</script>