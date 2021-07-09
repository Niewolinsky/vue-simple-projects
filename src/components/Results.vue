<template>
	<p>REACTION TIME: {{ score }} ms</p>
	<p>{{ rank }}</p>
</template>

<script setup>
import { onMounted, ref } from "vue";
let props = defineProps({
	score: Number,
});

let rank = ref(null);

onMounted(() => {
	if (props.score < 250) {
		rank.value = "FAST";
	} else if (props.score > 500) {
		rank.value = "SLOW";
	} else {
		rank.value = "MODERATE";
	}
});
</script>

<style lang='sass'>
</style>
