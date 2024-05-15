<script lang="ts">
	import { addTodo, genText } from '$lib/todos.svelte';

	let text = genText();

	function add() {
		addTodo(text);
		text = genText();
	}
</script>

<form on:submit|preventDefault={add}>
	<input class="input" bind:value={text} />
	<button class="button" type="submit"> Add Task </button>
</form>

<style lang="postcss">
	.input {
		border: 1px solid #d1d5db; /* Light grey border */
		padding: 0.5rem;
		border-radius: 0.5rem;
	}

	.button {
		border: 1px solid #d1d5db; /* Light grey border */
		padding: 0.5rem;
		border-radius: 0.5rem;
		background-color: #9333ea; /* Purple-600 */
		color: white;
		font-weight: 600;
		cursor: pointer;
	}

	.button:hover {
		opacity: 0.9;
	}
</style>
