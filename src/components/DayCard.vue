<script setup>
	import IconSun from './icons/IconSun.vue';
	import IconRain from './icons/IconRain.vue';
	import IconCloud from './icons/IconCloud.vue';
import { computed } from 'vue';

	const { weatrerCode, temp, date, isActive } = defineProps({
		weatrerCode: Number,
		temp: Number,
		date: Date,
		isActive: Boolean
	});
	const iconColor = computed(()=>{
		return isActive ? "var(--color-pimary-inverted)" : "var(--color-primary)"
	})
</script>

<template>
	<button class="day-card" :class="{active: isActive  }">
		<IconSun v-if="weatrerCode <= 1003" :color="iconColor "></IconSun>
		<IconCloud v-if="weatrerCode >= 1006 && weatrerCode < 1063"  :color="iconColor "></IconCloud>
		<IconRain v-if="weatrerCode >= 1063"  :color="iconColor "></IconRain>
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
		color: var(--color-primary);
		border-radius: 10px;
		box-shadow: 1px 2px 4px 0px #222831;
		border: none;
		cursor: pointer;
	}

	.active{
		color: var(--color-pimary-inverted);
		background-color: var(--color-primary);
	}

	.day-card:not(.active):hover {
		background-color: #3a434f;
	}

	/* .day-card__day {
	} */
</style>
