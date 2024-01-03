<template>
    <div :class="['absolute top-0 left-0 w-screen flex h-screen bg-gray-500/50 my-auto', { hidden: !open }]">
        <div class="max-w-md m-auto border rounded-lg w-80">
            <div class="flex flex-col p-5 bg-white rounded-lg shadow">
                <div class="flex">
                    <div>
                        <ExclamationTriangleIcon class="w-6 text-red-500" />
                    </div>
                    <div class="ml-3">
                        <h2 class="font-semibold text-gray-800">Error</h2>
                        <ul class="mt-2 text-sm leading-relaxed text-gray-600">
                            <li class="list-disc" v-for="(error, index) in errors" :key="index">
                                {{ error }}
                            </li>
                        </ul>
                    </div>
                </div>
                <div class="flex items-center justify-end mt-3">
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
import { ExclamationTriangleIcon } from '@heroicons/vue/24/outline'

const emit = defineEmits(['confirm'])

defineProps({
    errors: Array,
    open: Boolean
})

const acceptAction = () => {
    emit('confirm')
}
</script>