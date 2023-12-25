<template>
    <main class="px-10 py-5 m-5 bg-gray-100 rounded-xl max-w-[600px]" >
        <WeekView />
        <ListItems />
    </main>
</template>

<script setup>
import WeekView from '@/components/date/WeekView'
import ListItems from './ListItems.vue';
</script>