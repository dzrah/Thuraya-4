<script>
	import Container from './Container.svelte';
	import Section from './Section.svelte';

	let isOpen = $state(false);

	function toggleMenu() {
		isOpen = !isOpen;
	}

	function closeMenu() {
		isOpen = false;
	}
</script>

<Section bgClass="bg-[#121a6b]" class="z-50 fixed top-0 left-0 right-0">
	<Container>
		<nav
			class="flex items-center justify-between flex-1 text-white py-10 w-full h-full text-[0.9rem]"
		>
			<div class="flex justify-start items-start w-auto h-full">
				<a href="/" class="flex items-center justify-start"
					><img class="w-35" src="/Logo.svg" alt="" /></a
				>
			</div>

			<button
				onclick={toggleMenu}
				class="lg:hidden flex flex-col items-center justify-center w-10 h-10 gap-1.5"
				aria-label="Menu"
				><span
					class="w-6 h-0.5 bg-white transition-all duration-300 {isOpen
						? 'rotate-45 translate-y-2'
						: ''}"
				></span>
				<span class="w-6 h-0.5 bg-white transition-all duration-300 {isOpen ? 'opacity-0' : ''}"
				></span>
				<span
					class="w-6 h-0.5 bg-white transition-all duration-300 {isOpen
						? '-rotate-45 -translate-y-2'
						: ''}"
				></span></button
			>

			<div class="hidden lg:flex items-center justify-between h-full w-auto gap-10 font-extralight">
				<a href="#next-gen">Next Gen Satellite</a>
				<a href="#products">Products</a>
				<a href="#industry">Industries</a>
			</div>
			<div class="hidden lg:flex">
				<a
					class="bg-white p-2 text-[#121a6b] rounded-1xl font-extralight cursor-pointer hover:bg-[#0a82dc] transition-all duration-100 hover:text-white"
					href="#contact">Contact Us</a
				>
			</div>
		</nav>
	</Container>

	{#if isOpen}
		<div class="lg:hidden bg-[#121a6b] border-t border-white/10 flex">
			<Container>
				<div class="flex flex-col py-4 gap-4 font-extralight text-white">
					<a href="#next-gen" class="py-2 hover:opacity-80 transition-opacity" onclick={closeMenu}>
						Next Gen Satellite
					</a>
					<a href="#products" class="py-2 hover:opacity-80 transition-opacity" onclick={closeMenu}>
						Products
					</a>
					<a href="#industry" class="py-2 hover:opacity-80 transition-opacity" onclick={closeMenu}>
						Industries
					</a>
					<a
						href="#contact"
						class="bg-white px-4 py-2 text-[#121a6b] rounded-1xl text-center hover:bg-opacity-90 transition-all"
						onclick={closeMenu}
					>
						Contact Us
					</a>
				</div>
			</Container>
		</div>
	{/if}
</Section>
