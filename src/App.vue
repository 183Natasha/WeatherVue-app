<script setup>
import AppButton from './components/Button/AppButton.vue';
import ApppStat from './components/ApppStat.vue';


</script>

<template>
    <main class="main">
        <ApppStat label="Влажность" stat="90%"></ApppStat>
        <ApppStat label="Осадки" stat="0%"></ApppStat>
        <ApppStat label="Ветер" stat="3 м/ч"></ApppStat>
        <AppButton>
            Сохранить
        </AppButton>
    </main>

</template>

<style scoped>
.main {
    background: var(--color-bg-main);
    padding: 60px 50px;
    border-radius: 50px;
}
</style>
