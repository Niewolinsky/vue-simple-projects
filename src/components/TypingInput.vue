<template>
	<input
		:class="{ matches: validateInput() }"
		@keypress.enter="readInput"
		type="text"
		v-model="userInput"
	/>
</template>

<script setup>
import { ref } from "vue";

let props = defineProps({
	currentWord: String,
});

let emit = defineEmits(["next-word"]);

let userInput = ref("");

function readInput() {
	if (userInput.value === props.currentWord) {
		emit("next-word");
		userInput.value = "";
	}
}

function validateInput() {
	let typedText = new RegExp(`^${userInput.value}`, "m");
	return !typedText.test(props.currentWord);
}
</script>

<style lang='sass'>
.matches
	color: red
</style>
