<script lang="ts">
	import { deleteTodo, updateTodo } from '$lib/todos.svelte';

	export let todo: Todo;

	function remove() {
		deleteTodo(todo.id);
	}

	function toggleStatus() {
		updateTodo(todo.id, !todo.complete);
	}
</script>

<span class:text-complete={todo.complete}>
	{todo.text}
</span>
<span class:text-complete={todo.complete}>
	{todo.id}
</span>

{#if todo.complete}
	<button class="status-button" on:click={toggleStatus}> ✔️ </button>
{:else}
	<button class="status-button" on:click={toggleStatus}> ❌ </button>
{/if}

<button class="remove-button" on:click={remove}> 🗑 </button>

<style lang="postcss">
	.text-complete {
		color: #16a34a; /* Green-600 */
		text-decoration: line-through;
	}

	.status-button {
		cursor: pointer;
		background: none;
		border: none;
		font-size: 1rem;
	}

	.remove-button {
		cursor: pointer;
		background: none;
		border: none;
		font-size: 1rem;
		color: red;
	}
</style>
