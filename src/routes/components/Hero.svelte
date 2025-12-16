<script>
	import Container from './Container.svelte';
	import Section from './Section.svelte';
</script>

<Section class="reltaive flex items-center justify-center">
	<div class="w-full h-full object-cover flex items-center justify-center">
		<video loop autoplay muted playsinline class="flex w-full h-full" src="/bg_earth_1.mp4">
			<track kind="captions" />
		</video>
	</div>

	<Container class="absolute flex justify-center items-center">
		<div
			class="flex-col w-full h-full items-center justify-center md:mb-7 lg:mt-0 lg:mb-40 text-amber-50"
		>
			<h1
				class="font-antarctica font-semibold text-[1.2rem] sm:text-[1.3rem] md:text-[1.5rem] lg:text-[2.5rem] xl:text-[2.2rem] 2xl:text-[2.5rem]"
			>
				THURAYA-4
			</h1>
			<div class="flex-col text-[0.4rem] sm:text-[0.6rem] lg:text-[0.9rem] xl:text-[1.2rem]">
				<div>
					<p class="font-antartica font-light">CONNECTING WHAT MATTERS.</p>
				</div>
				<div>
					<p class="font-antartica font-light">SPACE-BASED. EARTH-FOCUSED.</p>
				</div>
			</div>
		</div>

		<div class="flex items-center justify-center w-full h-full">
			<img
				class=" mt-10 w-35 sm:mt-15 sm:w-55 md:w-65 lg:w-95 md:mt-20 lg:mt-30 xl:mt-50 xl:w-315 2xl:mt-50 2xl:w-1200"
				src="/satellite.png"
				alt=""
			/>
		</div>
	</Container>
</Section>
