<script>
	let { title, svgSrc, para } = $props();
</script>

<div class="flex-col w-full items-center justify-center lg:justify-start">
	<div class="flex lg:justify-start justify-center">
		<img class="lg:w-10 lg:h-10 w-10 h-10" src={svgSrc} alt="" />
	</div>
	<div class=" flex lg:justify-start justify-center mt-8">
		<p class="text-[#121a6b] font-semibold sm:text-[0.9rem] text-[0.8rem]">{title}</p>
	</div>
	<div
		class="mt-4 lg:text-[0.8rem] text-[0.7rem] flex lg:justify-start justify-center text-center lg:text-left sm:h-28 h-15 line-clamp-3"
	>
		<p>
			{para}
		</p>
	</div>
</div>
