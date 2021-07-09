<template>
	<h1>Vue 3 Todo App</h1>
	<AddTodo @addNewTodo="addNewTodo" />
	<ListTodos
		:todosArray="todosArray"
		@toggleDone="toggleDone"
		@togglePriority="togglePriority"
		@removeTodo="removeTodo"
	/>
</template>

<script setup>
import AddTodo from "./components/AddTodo.vue";
import ListTodos from "./components/ListTodos.vue";
import { ref } from "vue";

let todosArray = ref([]);

function addNewTodo(todoObject) {
	todosArray.value.push(todoObject);
}

function toggleDone(todo) {
	todo.isDone = !todo.isDone;
}

function togglePriority(todo) {
	todo.isHighPriority = !todo.isHighPriority;
}

function removeTodo(todo) {
	todosArray.value.splice(todosArray.value.indexOf(todo), 1);
}
</script>

<style lang='sass'>
.done
	text-decoration: line-through

.highPriority
	color: red
</style>
