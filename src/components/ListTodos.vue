<template>
	<ul>
		<li
			v-for="todo in todosArray"
			v-bind:key="todo.id"
			:class="{ done: todo.isDone, highPriority: todo.isHighPriority }"
		>
			{{ todo.content }}
			<button @click="$emit('toggleDone', todo)">TOGGLE DONE</button>
			<button @click="$emit('togglePriority', todo)">
				TOGGLE HIGH PRIORITY
			</button>
			<button @click="$emit('removeTodo', todo)">REMOVE</button>
		</li>
	</ul>
</template>

<script setup>
defineProps({
	todosArray: Array,
});
</script>
