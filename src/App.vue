<template>
	<h1>Vue 3 Click Reaction Game</h1>
	<button @click="start" :disabled="isPlaying">PLAY</button>
	<Block v-if="isPlaying" :delay="delay" @end="endGame" />
	<Results v-if="showResults" :score="score" />
</template>

<script setup>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
import { ref } from "vue";

let isPlaying = ref(false);
let delay = ref(null);
let score = ref(null);
let showResults = ref(false);

function start() {
	delay.value = Math.floor(2000 + Math.random() * 5000);
	isPlaying.value = true;
	showResults.value = false;
}

function endGame(reactionTime) {
	score.value = reactionTime;
	isPlaying.value = false;
	showResults.value = true;
}
</script>

<style lang='sass'>
</style>
