<template>
    <ModalBase @cancel="cancelAction" @confirm="confirmAction" :title="modalConfig.title" :content="modalConfig.content" :open="open"/>
</template>
  
<script setup>
import { defineProps, defineEmits } from 'vue';
import ModalBase from '@/components/modals/ModalBase'

const modalConfig = {
    title: "¿Finalizar?",
    content: "Confirmar"
}

const emit = defineEmits(['onCancel', 'onConfirm'])

defineProps({
    open: Boolean,
})

const cancelAction = () => {
    emit('onCancel')
}

const confirmAction = () => {
    emit('onConfirm')
}
</script>