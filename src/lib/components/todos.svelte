<script lang="ts">
	import { fly } from 'svelte/transition';
	import { useTodos } from '$lib/todos.svelte';
	import TodoItem from '@components/todo-item.svelte';
	import TodoForm from './todo-form.svelte';

	const _todos = useTodos();
	const todos = $derived(_todos.value);
</script>

{#if todos.data?.length}
	<div
		class="todo-grid"
		in:fly={{ x: 900, duration: 500 }}
	>
		{#each todos.data || [] as todo (todo.id)}
			<TodoItem {todo} />
		{/each}
	</div>
{:else if todos.loading}
	<p>Loading...</p>
{:else if todos.error}
	<p class="error">{todos.error}</p>
{:else}
	<p><b>Add your first todo item!</b></p>
{/if}

<TodoForm />

<style lang="postcss">
	.todo-grid {
		display: grid;
		grid-template-columns: repeat(4, auto);
		gap: 0.75rem;
		justify-items: start;
	}

	.error {
		color: #f87171; /* Red-500 */
	}
</style>
