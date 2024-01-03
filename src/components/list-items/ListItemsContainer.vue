<template>
    <main class="container px-10 py-5 mx-auto bg-gray-100 sm:my-5 sm:rounded-xl">
        <ListItemsHeader title="Compra semanal" @open-clear-list-modal="openClearListModal()"
            @toggle-editable="toggleEditable()" :disabled="isEmptyList" :editable="isEditable" />
        <ListItemsActions @add-item="addItem" />
        <ListItemsList :list="itemList" @buy-item="markItemAsDone" @delete-item="deleteListItem" :editable="isEditable" />
    </main>

    <!-- Modals -->
    <!-- Clear List Modal -->
    <ConfirmModal @close-modal="closeClearListModal()" @confirm="clearList" @cancel="closeClearListModal"
        :open="isOpenClearListModal" :title="'Finalizar'" :content="'Confirmar'" />
    <!-- Add Item Errors Modal -->
    <ErrorsModal @close-modal="closeErrorModal()" @confirm="closeErrorModal" :open="isOpenErrorModal"
        :errors="addItemErrors" />
</template>

<script setup>
import { ref, computed } from 'vue'
import ListItemsHeader from './ListItemsHeader.vue'
import ListItemsList from './ListItemsList.vue'
import ConfirmModal from '@/components/modals/ConfirmModal.vue'
import ErrorsModal from '@/components/modals/ErrorsModal.vue'
import ListItemsActions from './ListItemsActions.vue'

const isOpenClearListModal = ref(false)
const isOpenErrorModal = ref(false)

const isEditable = ref(false)

const addItemErrors = ref([])

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
    }
])

const openClearListModal = () => {
    isOpenClearListModal.value = true
}

const closeClearListModal = () => {
    isOpenClearListModal.value = false
}

const openErrorModal = () => {
    isOpenErrorModal.value = true
}

const closeErrorModal = () => {
    isOpenErrorModal.value = false
}

const isEmptyList = computed(() => {
    return itemList.value.length <= 0
})

function markItemAsDone(itemId) {
    itemList.value.map(item => { if (item.id === itemId) { item.done = !item.done } })
}

function deleteListItem(itemId) {
    itemList.value = itemList.value.filter(item => item.id !== itemId)
}

function addItem(itemName) {
    addItemErrors.value = []

    if (itemName === '') {
        addItemErrors.value.push('No se puede añadir un elemento vacio')
    }

    const elementExists = itemList.value.filter(item => item.name === itemName)

    if (elementExists.length > 0) {
        addItemErrors.value.push('No se puede añadir un elemento dos veces')
    }

    if (addItemErrors.value.length > 0) {
        openErrorModal()
        return
    }

    itemList.value.push({
        id: itemList.value.length + 1,
        name: itemName,
        done: false
    })
}

function clearList() {
    itemList.value = []
    isEditable.value = false
    closeClearListModal()
}

function toggleEditable() {
    isEditable.value = !isEditable.value
}
</script>