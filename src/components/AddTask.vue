<template>
	<form @submit.prevent="onSubmit">
		<div>
			<label>Task</label>
			<input
				type="text"
				v-model="text"
				name="text"
				placeholder="Add Task"
			/>
		</div>
		<div>
			<label>Day & Time</label>
			<input
				type="text"
				v-model="day"
				name="day"
				placeholder="Add Day & Time"
			/>
		</div>
		<div>
			<label>Set Reminder</label>
			<input type="checkbox" v-model="reminder" name="reminder" />
		</div>

		<input type="submit" value="Save Task" />
	</form>
</template>

<script setup>
import { ref } from "vue";

let text = ref("");
let day = ref("");
let reminder = ref(false);
let emit = defineEmits(["add-task"]);

function onSubmit() {
	if (!text.value) {
		alert("Please add a task");
	}

	const newTask = {
		id: Math.floor(Math.random() * 100000),
		text: text.value,
		day: day.value,
		reminder: reminder.value,
	};

	emit("add-task", newTask);
	text.value = "";
	day.value = "";
	reminder.value = false;
}
</script>

<style lang='sass'>
</style>
