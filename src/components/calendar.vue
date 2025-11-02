<script setup lang="ts">
import { ref } from 'vue';

import ButtonIcon from './button-icon.vue';

import ChevronLeftIcon from '../icons/chevron-left-icon.vue';
import ChevronRightIcon from '../icons/chevron-right-icon.vue';
import LangIcon from '../icons/lang-icon.vue';

const weekdays = ref(['Пн', 'Вт', 'Ср', 'Чт', 'Пт', 'Сб', 'Вс']);
const days = ref(Array.from({ length: 31 }, (_, i) => i + 1));

const selectedDay = ref<number | null>(null);

const selectDay = (day: number) => {
	selectedDay.value = day;
};
</script>

<template>
	<div class="calendar">
		<div class="header">
			<div class="header__controls">
				<ButtonIcon><ChevronLeftIcon /></ButtonIcon>
				<div class="header-title">Ноябрь 2025</div>
				<ButtonIcon><ChevronRightIcon /></ButtonIcon>
			</div>
			<ButtonIcon>
				<LangIcon width="20" height="20" />
			</ButtonIcon>
		</div>

		<div class="weekdays">
			<span v-for="(day, i) in weekdays" :key="i" class="weekday">{{ day }}</span>
		</div>

		<div class="days-grid">
			<button
				v-for="day in days"
				:key="day"
				type="button"
				class="day"
				:class="{ 'day--selected': selectedDay === day }"
				@click="selectDay(day)"
			>
				{{ day }}
			</button>
		</div>
	</div>
</template>

<style scoped>
.calendar {
	width: 400px;
	aspect-ratio: 1 / 1;
	border: 1px solid #161616;
	border-radius: 16px;
	background: #fff;
	padding: 16px;
}

.header {
	display: flex;
	justify-content: space-between;
	align-items: flex-start;
	gap: 12px;
}

.header__controls {
	display: flex;
	align-items: center;
	justify-content: center;
	gap: 24px;
}

.header-title {
	text-transform: uppercase;
	font-weight: 600;
	font-size: 26px;
}

.weekdays {
	display: grid;
	grid-template-columns: repeat(7, 1fr);
	text-align: center;
	margin-top: 16px;
	padding: 8px 0;
	border-bottom: 1px solid #e5e5e5;
}

.weekday {
	font-weight: 600;
	font-size: 16px;
	color: #222;
	text-transform: uppercase;
}

.days-grid {
	display: grid;
	grid-template-columns: repeat(7, 1fr);
	gap: 6px;
	padding-top: 12px;
}

.day {
	display: flex;
	align-items: center;
	justify-content: center;

	border: none;
	background: none;

	width: 100%;
	aspect-ratio: 1 / 1;

	border-radius: 8px;

	font-size: 15px;
	color: #222;
	transition: color 0.2s ease;
}

.day:hover {
	color: #ed5461;
	cursor: pointer;
}

.day--selected {
	border: 2px solid #ed5461;
	color: #ed5461;
	background: #fff;
}
</style>
