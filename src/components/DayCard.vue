<script setup>
	import IconSun from './icons/IconSun.vue';
	import IconRain from './icons/IconRain.vue';
	import IconCloud from './icons/IconCloud.vue';

	const { weatrerCode, temp, date } = defineProps({
		weatrerCode: Number,
		temp: Number,
		date: Date,
	});
</script>

<template>
	<button class="day-card">
		<IconSun v-if="weatrerCode == 1000"></IconSun>
		<IconRain v-if="weatrerCode == 1009 || weatrerCode == 1240"></IconRain>
		<IconCloud v-if="weatrerCode == 1003"></IconCloud>
		<div class="day-card__day">
			{{ date.toLocaleDateString('ru-RU', { weekday: 'short' }) }}
		</div>
		<div class="day-card__temp">{{ temp }} °C</div>
	</button>
</template>

<style scoped>
	.day-card {
		width: 100%;
		padding: 20px 24px;
		background-color: var(--color-bg-card);
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		gap: 15px;
		/* color: var(--color-pimary-inverted); */
		color: white;
		border-radius: 10px;
		box-shadow: 1px 2px 4px 0px #222831;
		border: none;
		cursor: pointer;
	}

	.day-card:hover {
		background-color: #3a434f;
	}

	/* .day-card__day {
	} */
</style>
