<script lang="ts">
	import { useUser } from '$lib/user.svelte';

	const user = useUser();

	const userData = $derived(user.value.data);
</script>

{#if userData}
	<div class="profile-container">
		<h3 class="greeting">Hi {userData.displayName}!</h3>

		{#if userData.photoURL}
			<img src={userData.photoURL} height="100" width="100" alt="user avatar" />
		{/if}
		<p>Your userID is {userData.uid}</p>
	</div>
{/if}

<style lang="postcss">
	.profile-container {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 0.75rem;
	}

	.greeting {
		font-size: 1.5rem;
		font-weight: bold;
	}
</style>
