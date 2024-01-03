<template>
    <div class="flex items-center justify-between py-2 pb-5 align-middle border-b">
        <div class="flex items-center justify-center gap-4 align-middle">
            <QueueListIcon class="w-6" />
            <h1 class="text-2xl font-bold leading-7 text-center text-gray-800">
                {{ title }}
            </h1>
        </div>
        <div class="hidden lg:flex">
            <ul class="flex flex-row gap-6">
                <li @click="toggleEditable" :disabled="disabled" :class="['cursor-pointer inline-flex items-center px-4 py-2', { 'hover:text-blue-600': !disabled, 'text-gray-400  cursor-not-allowed': disabled }]">
                    <PencilSquareIcon class="w-5 mr-3" />
                    <span v-if="!editable">Editar lista</span>
                    <span v-else>Finalizar edición</span>
                </li>
                <li @click="openClearListModal" :disabled="disabled"
                    :class="['cursor-pointer inline-flex items-center px-4 py-2', { 'hover:text-blue-600': !disabled, 'text-gray-400  cursor-not-allowed': disabled }]">
                    <ShoppingCartIcon class="w-5 mr-3" />
                    <span class="">Vaciar lista</span>
                </li>
            </ul>
        </div>
        <div class="flex lg:hidden">
            <button type="button" class="-m-2.5 inline-flex items-center justify-center rounded-md p-2.5 text-gray-700"
                @click="actionsMenuOpen = true">
                <span class="sr-only">Abrir menu de acciones</span>
                <EllipsisVerticalIcon class="w-5 text-gray-600" />
            </button>
        </div>
    </div>
    <div :class="['absolute top-0 left-0 w-screen h-screen', , { hidden: !actionsMenuOpen }]"
        @click="actionsMenuOpen = false">
        <div class="absolute w-auto px-2 bg-white rounded-lg right-10 top-32 lg:hidden">
            <ul class="flex flex-col divide-y divide-gray-500/10">
                <li @click="toggleEditable" :disabled="disabled" :class="['cursor-pointer inline-flex items-center px-4 py-2', { 'hover:text-blue-600': !disabled, 'text-gray-400  cursor-not-allowed': disabled }]">
                    <PencilSquareIcon class="w-5 mr-3" />
                    <span v-if="!editable">Editar lista</span>
                    <span v-else>Finalizar edición</span>
                </li>
                <li @click="openClearListModal" :disabled="disabled"
                    :class="['cursor-pointer inline-flex items-center px-4 py-2', { 'hover:text-blue-600': !disabled, 'text-gray-400  cursor-not-allowed': disabled }]">
                    <ShoppingCartIcon class="w-5 mr-3" />
                    <span class="">Vaciar lista</span>
                </li>
            </ul>
        </div>
    </div>
</template>

<script setup>
import { defineProps, defineEmits, ref } from 'vue'
import { EllipsisVerticalIcon } from "@heroicons/vue/16/solid"
import { ShoppingCartIcon, PencilSquareIcon, QueueListIcon } from '@heroicons/vue/24/outline'

const emit = defineEmits(['openClearListModal', 'toggleEditable'])

let props = defineProps({
    title: String,
    disabled: Boolean,
    editable: Boolean
})

const actionsMenuOpen = ref(false)

const openClearListModal = () => {
    if (props.disabled) { return }
    emit('openClearListModal')
}

const toggleEditable = () => {
    if (props.disabled) { return }
    emit('toggleEditable')
}
</script>