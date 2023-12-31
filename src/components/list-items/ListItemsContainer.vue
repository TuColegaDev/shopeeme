<template>
    <main class="container px-10 py-5 mx-auto bg-gray-100 sm:my-5 sm:rounded-xl">
        <ListTitle title="Compra semanal" />
        <ListItems :list="itemList" @buy-item="markItemAsDone" @delete-item="deleteListItem"/>
        <ListActions @open-clear-list-modal="openModal()" />
        <ClearListModal @close-modal="closeModal()" @on-confirm="clearList" @on-cancel="closeModal"
            :open="openClearListModal" />
    </main>
</template>

<script setup>
// import WeekView from '@/components/date/WeekView'
import { ref } from 'vue'
import ListTitle from './ListItemsTitle.vue';
import ListItems from './ListItemsList.vue';
import ListActions from './ListItemsActions.vue';
import ClearListModal from './ClearListItemsModal.vue'

const openClearListModal = ref(false);
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

const openModal = () => {
    openClearListModal.value = true;
}

const closeModal = () => {
    openClearListModal.value = false;
}

function markItemAsDone(itemId) {
    itemList.value.map(item => { if (item.id === itemId) { item.done = !item.done } });
}

function deleteListItem(itemId) {
    itemList.value = itemList.value.filter(item => item.id !== itemId);
}

const clearList = () => {
    itemList.value = [];
    closeModal();
}
</script>