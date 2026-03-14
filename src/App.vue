<script setup>
import { ref, reactive, computed } from 'vue';
import ApppStat from './components/ApppStat.vue';
import CitySelect from './components/CitySelect.vue';


let savedCity = ref("Moscow")

let arr = ref([1, 2, 3])
let obj = ref({ name: "Nata", age: "30" })

let data = ref({
    humidity: 90
})

let deteModified = computed(() => {
    return {
        label: 'Влажность',
        stat: data.value.humidity + "%"
    }
})

function getCity(city) {
    console.log(city)
    savedCity.value = city
    data.value.humidity = 20
}
</script>

<template>
    <ul>
        <li v-for="(number, index) in arr" :key="number">
            {{ index }}: {{ number }}
        </li>
    </ul>
    <ul>
        <li v-for="(name, key, index) in obj" :key="name">
            {{ index }}-{{ name }}: {{ key }}
        </li>
    </ul>
    <main class="main">
        {{ savedCity }}
        <ApppStat v-bind="deteModified"></ApppStat>
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
