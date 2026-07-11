<script setup>
	import IconSun from './icons/IconSun.vue';
	import IconRain from './icons/IconRain.vue';
	import IconCloud from './icons/IconCloud.vue';
	import { cityProvide } from '../constants.js';
	import { computed, inject } from 'vue';
	import IconLocation from './icons/IconLocation.vue';

	const { dayData, dayText } = defineProps({
		dayData: Object,
	});

	const city = inject(cityProvide);

	const day = computed(() => {
		return new Date(dayData.date).toLocaleDateString('ru-RU', {
			weekday: 'long',
		});
	});

	const date = computed(() => {
		return new Date(dayData.date).toLocaleDateString('ru-RU', {
			year: 'numeric',
			month: 'long',
			day: 'numeric',
		});
	});

	const weatrerCode = computed(() => {
		return dayData.day.condition.code;
	});
</script>

<template>
	<div class="left-panel">
		<div class="top">
			<div class="day">
				{{ day }}
			</div>

			<div class="date">
				{{ date }}
			</div>

			<div class="city">
				<IconLocation class="location"></IconLocation>
				{{ city }}
			</div>
		</div>

		<div class="left-panel__down">
			<div class="icon">
				<IconSun
					v-if="weatrerCode <= 1003"
					size="95"
				></IconSun>
				<IconCloud
					v-if="weatrerCode >= 1006 && weatrerCode < 1063"
					size="95"
				></IconCloud>
				<IconRain
					v-if="weatrerCode >= 1063"
					size="95"
				></IconRain>
			</div>

			<div class="temp">{{ dayData.day.avgtemp_c }} °C</div>

			<div class="text">
				{{ dayData.day.condition.text }}
			</div>
		</div>
	</div>
</template>

<style scoped>
	.left-panel {
		display: flex;
		flex-direction: column;
		padding: 48px 32px;
		justify-content: space-between;
		height: 100%;
	}

	.top {
		display: flex;
		flex-direction: column;
	}

	.day {
		font-weight: 700;
		font-size: 37px;
		text-transform: capitalize;
		margin-bottom: 16px;
	}

	.date {
		font-weight: 500;
		font-size: 22px;
		margin-bottom: 10px;
	}

	.city {
		display: flex;
		gap: 8px;
		font-weight: 600;
		font-size: 20px;
		align-items: center;
	}

	.location {
		width: 27px;
		height: 27px;
	}

	.left-panel__down {
		display: flex;
		flex-direction: column;
	}

	.icon {
		margin: 25px;
	}

	.temp {
		font-weight: 700;
		font-size: 50px;
		margin-bottom: 13px;
	}

	.text {
		font-weight: 700;
		font-size: 30px;
		margin-bottom: 39px;
	}
</style>
