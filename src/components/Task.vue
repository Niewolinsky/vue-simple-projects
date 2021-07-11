<template>
	<div
		@dblclick="emit('toggle-reminder', task.id)"
		:class="[task.reminder ? 'reminder' : '']"
	>
		<h3>{{ task.text }}</h3>
		<p>{{ task.day }}</p>
		<button @click="emit('delete-task', task.id)">X</button>
	</div>
</template>

<script setup>
defineProps({
	task: Object,
});

let emit = defineEmits(["delete-task", "toggle-reminder"]);
</script>

<style lang='sass'>
.reminder
	color: green
</style>
