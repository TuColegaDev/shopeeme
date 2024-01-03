<template>
    <div :class="['absolute top-0 left-0 w-screen h-screen bg-gray-500/50 my-auto', open ? 'flex' : 'hidden']">
        <div class="max-w-md m-auto border rounded-lg w-80">
            <div class="flex flex-col p-5 bg-white rounded-lg shadow">
                <div class="flex">
                    <div>
                        <ExclamationCircleIcon class="w-6 text-blue-500" />
                    </div>
                    <div class="ml-3">
                        <h2 class="font-semibold text-gray-800">{{ title }}</h2>
                        <p class="mt-2 text-sm leading-relaxed text-gray-600">{{ content }}</p>
                    </div>
                </div>
                
                <div class="flex items-center justify-end mt-3">
                    <button @click="cancelAction" class="px-4 py-2 text-sm font-medium text-gray-800 bg-gray-100 rounded-md hover:bg-gray-200">
                        Cancelar
                    </button>
                    
                    <button @click="acceptAction" class="px-4 py-2 ml-2 text-sm font-medium text-white bg-blue-500 rounded-md hover:bg-blue-600">
                        Aceptar
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>
  
<script setup>
import { defineProps, defineEmits } from 'vue'
import { ExclamationCircleIcon } from '@heroicons/vue/24/outline'

const emit = defineEmits(['cancel', 'confirm'])

defineProps({
    title: String,
    content: String,
    open: Boolean
})

const cancelAction = () => {
    emit('cancel')
}

const acceptAction = () => {
    emit('confirm')
}
</script>