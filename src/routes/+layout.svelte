<script>
	import '../app.pcss';
</script>

<slot />
<nav class="navigation">
	<a href="/">Home</a>
	<a href="/about">About</a>
</nav>

<style lang="postcss">
	.navigation {
		display: flex;
		gap: 0.75rem;
		justify-content: center;
		margin-top: 1.25rem;
	}
</style>
