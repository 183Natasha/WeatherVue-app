<script setup></script>

<template>
    <button class="btn">
        <span>
            <slot name="icon"></slot>
        </span>
        <slot></slot>
    </button>
</template>

<style scoped>
.btn {
    border: none;
    border-radius: 10px;
    background: var(--gradient);
    padding: 14px;
    font-family: var(--font);
    font-size: 20px;
    color: var(--color-primary);
    font-weight: 600;
    cursor: pointer;
    display: flex;
    gap: 9px;
    align-items: center;
}

.btn:hover {
    background: var(--gradient-inverted);
}
</style>