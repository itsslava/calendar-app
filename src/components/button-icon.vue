<template>
	<button class="button-icon">
		<slot />
	</button>
</template>

<style scoped>
.button-icon {
	display: flex;
	align-items: center;
	justify-content: center;

	width: 36px;
	height: 36px;
	border-radius: 8px;
	border: none;
	background: transparent;
	cursor: pointer;

	padding: 0;
	line-height: 0;

	border: none;
	background: none;

	transition: background 0.2s ease;
}

.button-icon:hover {
	background: rgba(0, 0, 0, 0.05);
}

.button-icon :deep(svg) {
	display: block;
}
</style>
