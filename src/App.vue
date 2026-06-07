<script setup>
import { ref, reactive, computed } from 'vue';
import ApppStat from './components/ApppStat.vue';
import CitySelect from './components/CitySelect.vue';


// let savedCity = ref("Moscow")

const API_ENDPOINT = 'https://api.weatherapi.com/v1'

let data = ref({
    humidity: 90,
    rain: 0,
    wind: 3
})

let deteModified = computed(() => {
    return [
        {
            label: 'Влажность',
            stat: data.value.humidity + "%"
        },
        {
            label: 'Осадки',
            stat: data.value.rain + "%"
        },
        {
            label: 'Ветер',
            stat: data.value.wind + "м/ч"
        }
    ]
})

async function getCity(city) {
    // console.log(city)
    // savedCity.value = city
    // data.value.humidity = 20
    const params= new URLSearchParams({
        q: city,
        lang: "ru",
        key: "98f183f1d1874d859ef103717260606",
        days: 3,
    })
    const res = await fetch (`${API_ENDPOINT}/forecast.json?${params.toString()}`)
    const data = await res.json()
    console.log(data)
}
</script>

<template>

    <main class="main">
        <div class="city">{{ savedCity }}</div>
        <ApppStat v-for="item in deteModified" :key="item.label" v-bind="item"></ApppStat>
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
