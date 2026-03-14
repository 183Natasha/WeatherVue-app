<script setup>
import { onMounted, onUnmounted, onUpdated } from 'vue';

const data = defineModel({ type: String, required: true })

onMounted(() => {
    console.log('Input mounted')
})

onUpdated(() => {
    console.log('Input - updated')
})

onUnmounted(() => {
    console.log('Input - unmounted')
})

</script>

<template>
    <input v-model="data" class="input">
</template>

<style scoped>
.input {
    width: 260px;
    height: 53px;
    border-radius: 10px;
    border: none;
    color: var(--color-primary);
    font-size: 18px;
    padding: 15px 20px;
    box-shadow: 1px 2px 4px 0 var(--color-bg-main);
    background: var(--color-bg-card);
}

.input::placeholder {
    color: var(--color-text-placeholder)
}
</style>