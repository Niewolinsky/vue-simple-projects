<template>
	<div class="block" v-if="showBlock" @click="stopTimer">click me</div>
</template>

<script setup>
import { ref, onMounted } from "@vue/runtime-core";

let showBlock = ref(false);
let timer = ref(null);
let reactionTime = ref(0);

let props = defineProps({
	delay: Number,
});

onMounted(mountCallback);
const emit = defineEmits(["end"]);

function mountCallback() {
	setTimeout(() => {
		showBlock.value = true;
		startTimer();
	}, props.delay);
}

function startTimer() {
	timer.value = setInterval(() => {
		reactionTime.value += 10;
	}, 10);
}

function stopTimer() {
	clearInterval(timer.value);
	emit("end", reactionTime.value);
}
</script>

<style lang='sass'>
.block
	width: 400px
	border-radius: 20px
	background: #0faf87
	color: white
	text-align: center
	padding: 100px 0
	margin: 40px auto
</style>
