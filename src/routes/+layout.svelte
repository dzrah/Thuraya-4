<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<!-- <nav class="w-full bg-blue-700 z-100000 h-30"></nav> -->

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

{@render children()}

<style>
	/* :global(html, body) {
		font-family: 'Antarctica', sans-serif;
		font-weight: 400;
	} */
</style>
