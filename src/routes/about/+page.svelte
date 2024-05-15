<script lang="ts">
	import type { PageData } from './$types';

	export let data: PageData;
</script>

<div class="container">
	<div class="content">
		<h1 class="title">{data.about.name}</h1>
		<p>{data.about.description}</p>
	</div>
</div>

<style lang="postcss">
	.container {
		display: flex;
		align-items: center;
		justify-content: center;
		margin: 1.25rem 0;
	}

	.content {
		border: 1px solid #d1d5db; /* Light grey border */
		width: 400px;
		padding: 1.25rem;
		display: flex;
		flex-direction: column;
		gap: 0.75rem;
	}

	.title {
		font-size: 1.875rem;
		font-weight: 600;
	}
</style>
