<script>
	let { title, svgSrc, para } = $props();
</script>

<div class="flex-col w-full items-center justify-center lg:justify-start">
	<div class="flex lg:justify-start justify-center items-center w-full">
		<img class="lg:w-50 lg:h-20 w-40 h-25 flex items-center justify-center" src={svgSrc} alt="" />
	</div>
	<div class=" flex lg:justify-start justify-center lg:mt-8 mt-0 lg:h-16 h-6">
		<p class="text-[#121a6b] font-semibold sm:text-[0.9rem] text-[0.8rem] text-center lg:text-left">
			{title}
		</p>
	</div>
	<div
		class="mt-4 lg:text-[0.8rem] text-[0.7rem] flex lg:justify-start justify-center text-center lg:text-left sm:h-28 h-10 line-clamp-3"
	>
		<p>
			{para}
		</p>
	</div>
</div>
