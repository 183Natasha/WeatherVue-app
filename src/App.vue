<script setup>
import ApppStat from './components/ApppStat.vue';
import CitySelect from './components/CitySelect.vue';


const data = {
    label: "Влажность",
    stat: "90%"
}

</script>

<template>
    <main class="main">
        <ApppStat v-bind="data"></ApppStat>
        <ApppStat label="Осадки" stat="0%"></ApppStat>
        <ApppStat label="Ветер" stat="3 м/ч"></ApppStat>
        <CitySelect></CitySelect>
        
    </main>

</template>

<style scoped>
.main {
    background: var(--color-bg-main);
    padding: 60px 50px;
    border-radius: 50px;
}
</style>
