<template>
    <div>
        <h1 class="text-xl font-bold text-center">
            Semana {{ weekNumber }} del año
        </h1>
        <div class="flex items-center">
            <div v-for="dateItem in dateItems" :key="dateItem.id" class="flex flex-col items-center justify-center w-1/2 p-5 sm:flex-row">
                <span class="mr-3 font-medium">
                    {{ dateItem.prefix }}
                </span>
                <span class="p-1 px-3 text-xl border border-gray-300 rounded bg-white/80">
                    {{ dateItem.date }} 
                </span>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'

const currentDate = new Date()
const startDate = new Date(currentDate.getFullYear(), 0, 1)
const days = Math.floor((currentDate - startDate) / (24 * 60 * 60 * 1000))

const firstWeekDay = currentDate.getDate() - currentDate.getDay()
const lastWeekDay = firstWeekDay + 6

const firstWeekDate = new Date(currentDate.setDate(firstWeekDay)).toLocaleDateString('es-ES')
const lastWeekDate = new Date(currentDate.setDate(lastWeekDay)).toLocaleDateString('es-ES')

const dateItems = ref([
    {
        id: 1,
        date: firstWeekDate,
        prefix: 'Del'
    },
    {
        id: 2,
        date: lastWeekDate,
        prefix: 'al'
    }
])

const weekNumber = ref(Math.ceil(days / 7))
</script>