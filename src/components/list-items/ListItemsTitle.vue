<template>
    <div class="border-b">
        <h1 class="p-4 mb-4 text-2xl font-bold text-center text-gray-600">
            {{ title }}
        </h1>
    </div>
</template>

<script setup>
import { defineProps } from 'vue'

defineProps({
    title: String
})
</script>