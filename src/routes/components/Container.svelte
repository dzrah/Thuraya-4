<script>
	let { class: className = '', children } = $props();
</script>

<div class="w-full max-w-6xl mx-auto px-20 sm:px-30 lg:px-25 {className}">
	{@render children()}
</div>
