<template>
	<header>
		<h1>{{ title }}</h1>
		<Button @toggle-add-task="emit('toggle-add-task')" text="Add Task" />
	</header>
</template>

<script setup>
import Button from "./Button.vue";
import { ref } from "vue";
defineProps({
	title: String,
});

let emit = defineEmits(["toggle-add-task"]);
</script>

<style lang='sass'>
</style>
