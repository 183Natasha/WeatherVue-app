<script setup>
const props = defineProps({
    error: String
})
</script>
<template>
    <div class="error" v-if='props.error'>{{ props.error }}</div>
</template>

<style>
.error {
    font-size: 18px;
    padding: 15px;
    background-color: var(--color-bg-card);
    text-align: center;
    border-radius: 0px 0px 25px 25px;
    margin-top: -60px;
    margin-bottom: 60px;
}
</style>