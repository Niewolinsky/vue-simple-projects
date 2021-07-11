<template>
	<Header @toggle-add-task="toggleAddTask" title="Vue 3 Tasker App" />
	<div v-if="showAddTask">
		<AddTask @add-task="addTask" />
	</div>
	<Tasks
		:tasks="tasks"
		@delete-task="deleteTask"
		@toggle-reminder="toggleReminder"
	/>
</template>

<script setup>
import { ref, onMounted } from "vue";
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import AddTask from "./components/AddTask.vue";

let tasks = ref([]);
let showAddTask = ref(false);

function deleteTask(id) {
	if (confirm("Are you sure?")) {
		tasks.value = tasks.value.filter((task) => task.id !== id);
	}
}

function toggleReminder(id) {
	tasks.value = tasks.value.map((task) =>
		task.id === id ? { ...task, reminder: !task.reminder } : task
	);
}

function toggleAddTask() {
	showAddTask.value = !showAddTask.value;
}

function addTask(task) {
	tasks.value = [...tasks.value, task];
}

onMounted(() => {
	tasks.value = [
		{
			id: 1,
			text: "Doctors Appointment",
			day: "March 1st at 2:30pm",
			reminder: true,
		},
		{
			id: 2,
			text: "Meeting at School",
			day: "March 2nd at 2:00pm",
			reminder: false,
		},
		{
			id: 3,
			text: "Food Shopping",
			day: "March 3rd at 4:45pm",
			reminder: true,
		},
	];
});
</script>

<style lang='sass'>
</style>
