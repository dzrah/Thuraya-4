<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';
	import Navbar from './components/Navbar.svelte';

	let { children } = $props();
</script>

<!-- <nav class="w-full bg-blue-700 z-100000 h-30"></nav> -->

<svelte:head>
	<title>Thuraya</title>
	<link rel="icon" href={favicon} />
</svelte:head>

<!-- <Navbar /> -->

{@render children()}

<style>
	/* :global(html, body) {
		font-family: 'Antarctica', sans-serif;
		font-weight: 400;
	} */
</style>
