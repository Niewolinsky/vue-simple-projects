<template>
	<button @click="emit('toggle-add-task')">{{ text }}</button>
</template>

<script setup>
defineProps({
	text: String,
});

let emit = defineEmits(["toggle-add-task"]);
</script>

<style lang='sass'>
</style>
