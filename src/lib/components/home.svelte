<script lang="ts">
	import { loginWithGoogle, logout } from '$lib/user.svelte';
	import Todos from '@components/todos.svelte';
	import Profile from '@components/profile.svelte';
	import { useUser } from '$lib/user.svelte';

	const _user = useUser();
	const user = $derived(_user.value);
</script>

<h1 class="header">Svelte 5 Firebase Todo App</h1>

<section class="container">
	{#if user.data}
		<Profile />
		<button class="logout-btn" onclick={logout}> Logout </button>
		<hr />
		<Todos />
	{:else if user.loading}
		<p>Loading...</p>
	{:else if user.error}
		<p class="error">Error: {user.error}</p>
	{:else}
		<button class="login-btn" onclick={loginWithGoogle}> Signin with Google </button>
	{/if}
</section>

<style lang="postcss">
	.header {
		margin: 1rem 0;
		font-size: 1.875rem;
		font-weight: 600;
		text-align: center;
	}

	.container {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 0.75rem;
		padding: 1.25rem;
	}

	.logout-btn,
	.login-btn {
		padding: 0.75rem;
		font-weight: 600;
		color: white;
		border: none;
		border-radius: 0.5rem;
		cursor: pointer;
	}

	.logout-btn {
		background-color: #2563eb; /* Blue-600 */
	}

	.login-btn {
		background-color: #dc2626; /* Red-600 */
	}

	.logout-btn:hover,
	.login-btn:hover {
		opacity: 0.9;
	}

	.error {
		color: #f87171; /* Red-500 */
	}
</style>
