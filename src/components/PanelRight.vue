<script setup>
	import Error from './Error.vue';
	import DayCard from './DayCard.vue';
	import CitySelect from './CitySelect.vue';
	import ApppStat from './ApppStat.vue';
	import { computed } from 'vue';
	import { errorMap } from '../constants.js';

	const { error, data, activeIndex } = defineProps({
		error: Object,
		data: Object,
		activeIndex: Number,
	});

	const emit = defineEmits(['select-index', 'select-city']);

	const errorDisplay = computed(() => {
		return errorMap.get(error?.error?.code);
	});

	let statData = computed(() => {
		if (!data) {
			return [];
		}
		return [
			{
				label: 'Влажность',
				stat: data.current.humidity + ' %',
			},
			{
				label: 'Облачность',
				stat: data.current.cloud + ' %',
			},
			{
				label: 'Ветер',
				stat: ((data.current.wind_kph * 1000) / 3600).toFixed(1) + ' м/с',
			},
		];
	});
</script>

<template>
	<Error
		v-if="error"
		:error="errorDisplay"
	></Error>
	<div
		v-if="data && data.current"
		class="stat-data"
	>
		<div class="stat-list">
			<ApppStat
				v-for="item in statData"
				:key="item.label"
				v-bind="item"
			></ApppStat>
		</div>

		<div class="day-card-list">
			<DayCard
				v-for="(item, i) in data.forecast.forecastday"
				:key="item.date"
				:weatrer-code="item.day.condition.code"
				:temp="item.day.avgtemp_c"
				:date="new Date(item.date)"
				:is-active="activeIndex == i"
				@click="() => emit('select-index', i)"
			></DayCard>
		</div>
	</div>

	<CitySelect></CitySelect>
</template>

<style>
	.stat-list {
		display: flex;
		flex-direction: column;
		gap: 16px;
	}

	.stat-data {
		display: flex;
		flex-direction: column;
		gap: 90px;
	}

	.day-card-list {
		display: flex;
		gap: 1px;
		margin-bottom: 70px;
	}
</style>
