<script setup>
import { ref } from 'vue';
import ApppStat from './components/ApppStat.vue';
import CitySelect from './components/CitySelect.vue';

let savedCity = ref("Moscow")

let data = ref({
    label: "Влажность",
    stat: "90%"
})

function getCity(city){
    console.log(city)
    savedCity.value = city
}
</script>

<template>
    <main class="main">
        {{ savedCity }}
        <ApppStat v-bind="data"></ApppStat>
        <ApppStat label="Осадки" stat="0%"></ApppStat>
        <ApppStat label="Ветер" stat="3 м/ч"></ApppStat>
        <CitySelect @select-city="getCity"></CitySelect>
        
    </main>

</template>

<style scoped>
.main {
    background: var(--color-bg-main);
    padding: 60px 50px;
    border-radius: 50px;
}
</style>
