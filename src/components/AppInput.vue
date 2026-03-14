<script setup></script>

<template>
    <input type="text" class="input">
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