<template>
	<h1>Vue 3 Typing Speed Game</h1>
	<button @click="toggleGameState">
		{{ isGameStarted ? "RESTART" : "START" }}
	</button>
	<div v-if="isGameStarted">
		<WordBlock :wordsArray="wordsArray" @stop-game="toggleGameState" />
		<Timer @stop-time="getTime" />
	</div>
	{{ lastGameTime }} s
</template>

<script setup>
import WordBlock from "./components/WordBlock.vue";
import Timer from "./components/Timer.vue";
import { ref, onMounted } from "vue";

onMounted(async () => {
	const response = await fetch(
		"https://api.quotable.io/quotes?limit=10&maxLength=40"
	);
	const data = await response.json();
	const content = data.results.map((item) => item.content);
	wordsArray.value = content;
});

let isGameStarted = ref(false);
let lastGameTime = ref(0);
let wordsArray = ref([]);

function toggleGameState() {
	isGameStarted.value = !isGameStarted.value;
}

function getTime(time) {
	lastGameTime.value = time.value;
}
</script>

<style lang='sass'>
</style>
