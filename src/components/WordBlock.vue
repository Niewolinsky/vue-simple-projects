<template>
	<h2>{{ currentWord }}</h2>
	<TypingInput :currentWord="currentWord" @next-word="nextWord" />
</template>

<script setup>
import TypingInput from "./TypingInput.vue";
import { computed, ref } from "vue";

let props = defineProps({
	wordsArray: Array,
});

let emit = defineEmits(["stop-game"]);

let currentWord = ref(props.wordsArray[0]);
let currentWordCount = ref(0);

function nextWord() {
	if (currentWordCount.value === wordsArrayMaxPosition.value) {
		emit("stop-game");
	}

	currentWord.value = props.wordsArray[++currentWordCount.value];
}

let wordsArrayMaxPosition = computed(() => {
	return props.wordsArray.length - 1;
});
</script>

<style lang='sass'>
</style>
