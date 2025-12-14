<script>
	let {
		class: className = '',
		bgClass = 'bg-white',
		bgImage = '',
		children,
		...restProps
	} = $props();
</script>

<section
	class="w-full {bgClass} {className}"
	style={bgImage ? `background-image: url(${bgImage})` : ''}
	{...restProps}
>
	{@render children()}
</section>
