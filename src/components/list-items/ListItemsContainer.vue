<template>
    <main class="container px-10 py-5 mx-auto bg-gray-100 sm:my-5 sm:rounded-xl">
        <ListItemsHeader title="Compra semanal"  @open-clear-list-modal="openModal()" :disabled="isEmptyList" />
        <ListItemsList :list="itemList" @buy-item="markItemAsDone" @delete-item="deleteListItem"/>
        <ClearListModal @close-modal="closeModal()" @on-confirm="clearList" @on-cancel="closeModal"
            :open="openClearListModal" />
    </main>
</template>

<script setup>
import { ref, computed } from 'vue'
import ListItemsHeader from './ListItemsHeader.vue';
import ListItemsList from './ListItemsList.vue';
import ClearListModal from './modals/ClearListItemsModal.vue'

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

const isEmptyList = computed(() => {
    return itemList.value.length <= 0;
})

const clearList = () => {
    itemList.value = [];
    closeModal();
}
</script>