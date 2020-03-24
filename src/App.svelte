<TodoList todos={todos}/>

<style>
	:global(html) {
		background-color: #f8f8fd;
	}
</style>

<script>
	import TodoList from './components/TodoList.svelte';
	import Tailwindcss from './utils/Tailwindcss.svelte';

	let todos = [
		{ todo: 'Todo 1', complete: false},
		{ todo: 'Todo 2', complete: true},
	]
</script>