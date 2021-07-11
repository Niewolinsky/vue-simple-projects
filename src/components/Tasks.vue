<template>
	<div v-for="task in tasks" :key="task.id">
		<Task
			@toggle-reminder="emit('toggle-reminder', task.id)"
			@delete-task="emit('delete-task', task.id)"
			:task="task"
		/>
	</div>
</template>

<script setup>
import Task from "./Task.vue";
defineProps({
	tasks: Array,
});
let emit = defineEmits(["delete-task", "toggle-reminder"]);
</script>

<style lang='sass'>
</style>
