<script setup>
	import { onMounted, provide, ref, watch } from 'vue';
	import PanelRight from './components/PanelRight.vue';
	import { API_ENDPOINT, cityProvide } from './constants.js';
	import PanelLeft from './components/PanelLeft.vue';

	let data = ref();
	let error = ref();
	let activeIndex = ref(0);
	const city = ref('Moscow');

	provide(cityProvide, city);

	watch(city, () => {
		getCity(city.value);
	});

	onMounted(() => {
		getCity(city.value);
	});

	async function getCity(city) {
		const params = new URLSearchParams({
			q: city,
			lang: 'ru',
			key: '98f183f1d1874d859ef103717260606',
			days: 3,
		});
		const res = await fetch(`${API_ENDPOINT}/forecast.json?${params.toString()}`);
		if (res.status != 200) {
			error.value = await res.json();
			data.value = null;
			console.log(error.value);
			return;
		}

		data.value = await res.json();
		error.value = null;
		// console.log(data.value)
	}
</script>

<template>
	<main class="main">
		<div class="left">
			<PanelLeft v-if="data"
				:day-data="data.forecast.forecastday[activeIndex ]"
			></PanelLeft>
		</div>
		<div class="right">
			<PanelRight
				:data
				:error
				:active-index="activeIndex"
				@select-index="(i) => (activeIndex = i)"
			></PanelRight>
		</div>
	</main>
</template>

<style scoped>
	.main {
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.right {
		background: var(--color-bg-main);
		padding: 60px 50px;
		border-radius: 0 25px 25px 0;
	}
	.left {
		width: 500px;
		height: 680px;
		border-radius: 30px;
		background-image: url('/bg.png');
		background-repeat: no-repeat;
		background-size: cover;
	}
</style>
