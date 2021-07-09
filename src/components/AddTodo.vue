<template>
	<form @submit.prevent="passTodoObject">
		<input v-model="todoContent" name="todoContent" />
		<button>Add New Todo</button>
	</form>
</template>

<script setup>
import { ref } from "vue";

let todoContent = ref("");

const emit = defineEmits(["addNewTodo"]);

function passTodoObject() {
	let obj = {
		id: Date.now(),
		isDone: false,
		isHighPriority: false,
		content: todoContent.value,
	};
	emit("addNewTodo", obj);

	todoContent.value = "";
}
</script>

<style lang='sass' scoped>
</style>
