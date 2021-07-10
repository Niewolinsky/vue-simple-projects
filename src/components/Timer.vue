<template>
	<p>{{ timeToSeconds }} s</p>
</template>

<script setup>
import { ref, onMounted, computed, onUnmounted } from "vue";

let time = ref(0);
let x = ref(null);
onMounted(startTime);
onUnmounted(stopTime);
let emit = defineEmits(["stop-time"]);

function startTime() {
	x = setInterval(() => {
		time.value += 10;
	}, 10);
}

function stopTime() {
	clearInterval(x);
	emit("stop-time", timeToSeconds);
}

let timeToSeconds = computed(() => {
	return time.value / 1000;
});
</script>

<style lang='sass'>
</style>
