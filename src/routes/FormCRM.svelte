<script>
	import { onMount } from 'svelte';
	import Section from './components/Section.svelte';
	import Container from './components/Container.svelte';

	onMount(() => {
		const script = document.createElement('script');
		script.src =
			'https://cxppusa1formui01cdnsa01-endpoint.azureedge.net/uae/FormLoader/FormLoader.bundle.js';
		script.onload = () => {
			// Run multiple times to catch async form rendering
			setTimeout(fixFormWidth, 500);
			setTimeout(fixFormWidth, 1000);
			setTimeout(fixFormWidth, 1500);
			setTimeout(fixFormWidth, 2000);
			setTimeout(fixFormWidth, 3000);
		};
		document.body.appendChild(script);

		// Also watch for DOM changes and reapply styles
		const observer = new MutationObserver(() => {
			fixFormWidth();
		});

		setTimeout(() => {
			const wrapper = document.querySelector('.dynamics-form-wrapper');
			if (wrapper) {
				observer.observe(wrapper, { childList: true, subtree: true });
			}
		}, 1000);

		return () => observer.disconnect();
	});

	function fixFormWidth() {
		const wrapper = document.querySelector('.dynamics-form-wrapper');
		if (!wrapper) return;

		// Force width on ALL inputs, textareas, selects
		wrapper.querySelectorAll('input, textarea, select').forEach((el) => {
			el.style.setProperty('width', '100%', 'important');
			el.style.setProperty('max-width', '100%', 'important');
			el.style.setProperty('box-sizing', 'border-box', 'important');
		});

		// Force width on form field blocks
		wrapper
			.querySelectorAll('.textFormFieldBlock, .optionSetFormFieldBlock, .phoneFormFieldBlock')
			.forEach((el) => {
				el.style.setProperty('width', '100%', 'important');
				el.style.setProperty('max-width', '100%', 'important');
				el.style.setProperty('padding-left', '0', 'important');
				el.style.setProperty('padding-right', '0', 'important');
			});

		// Force width on layout containers
		wrapper
			.querySelectorAll(
				'[data-layout="true"], .outer, table, th, td, .columnContainer, .inner, .containerWrapper, .tbContainer'
			)
			.forEach((el) => {
				el.style.setProperty('width', '100%', 'important');
				el.style.setProperty('max-width', '100%', 'important');
			});

		// Remove any hardcoded width attributes
		wrapper.querySelectorAll('[width]').forEach((el) => {
			el.removeAttribute('width');
		});

		// Fix any element with inline style containing width
		wrapper.querySelectorAll('[style*="width"]').forEach((el) => {
			el.style.setProperty('width', '100%', 'important');
			el.style.setProperty('max-width', '100%', 'important');
		});
	}
</script>

<Section bgClass="bg-[#f0f1f7]">
	<Container>
		<div class="form-section-wrapper">
			<!-- Left side: Your text content -->
			<div class="form-text-side">
				<div
					class="text-[#0e329b] font-semibold sm:text-[1.7rem] text-[1.3rem] w-full flex mb-6 text-center sm:text-left"
				>
					<h2>Start Your Thuraya-4 Deployment</h2>
				</div>
				<div
					class="font-antartica font-light sm:text-[1.2rem] text-[1rem] text-[#666666] mb-12 text-center sm:text-left"
				>
					<p>Speak with a specialist on products, services, and timelines</p>
				</div>
				<div
					class="font-antartica font-light text-[0.7rem] text-[#666666] mb-5 text-center sm:text-left"
				>
					<p>* Mandatory Field</p>
				</div>
			</div>

			<!-- Right side: Dynamics Form Container -->
			<div class="form-container-side">
				<div class="dynamics-form-wrapper">
					<div
						data-form-id="92e5516c-d6af-f011-bbd3-6045bd6abf1b"
						data-form-api-url="https://public-uae.mkt.dynamics.com/api/v1.0/orgs/b0843b43-2e40-ee11-94d3-6045bd6a6257/landingpageforms"
						data-cached-form-url="https://assets-uae.mkt.dynamics.com/b0843b43-2e40-ee11-94d3-6045bd6a6257/digitalassets/forms/92e5516c-d6af-f011-bbd3-6045bd6abf1b"
					></div>
				</div>
			</div>
		</div>
	</Container>
</Section>

<style>
	/* ============================================
     MAIN LAYOUT
     ============================================ */

	.form-section-wrapper {
		display: flex;
		flex-direction: column;
		width: 100%;
		gap: 2rem;
		padding: 6rem 0;
	}

	@media (min-width: 768px) {
		.form-section-wrapper {
			flex-direction: row;
			align-items: flex-start;
			gap: 3rem;
		}
	}

	.form-text-side {
		width: 100%;
		flex-shrink: 0;
	}

	@media (min-width: 768px) {
		.form-text-side {
			width: 35%;
			padding-right: 1rem;
		}
	}

	.form-container-side {
		width: 100%;
		min-width: 0;
	}

	@media (min-width: 768px) {
		.form-container-side {
			width: 65%;
		}
	}

	/* ============================================
     DYNAMICS FORM - AGGRESSIVE FULL WIDTH
     ============================================ */

	.dynamics-form-wrapper {
		width: 100% !important;
		max-width: 100% !important;
	}

	.dynamics-form-wrapper :global(*) {
		max-width: 100% !important;
		box-sizing: border-box !important;
	}

	.dynamics-form-wrapper :global([data-layout='true']),
	.dynamics-form-wrapper :global(table),
	.dynamics-form-wrapper :global(.outer),
	.dynamics-form-wrapper :global(th),
	.dynamics-form-wrapper :global(td),
	.dynamics-form-wrapper :global(.columnContainer),
	.dynamics-form-wrapper :global(.inner),
	.dynamics-form-wrapper :global(.containerWrapper),
	.dynamics-form-wrapper :global(.tbContainer) {
		width: 100% !important;
		max-width: 100% !important;
	}

	/* Hide Dynamics headings */
	.dynamics-form-wrapper :global([data-editorblocktype='Text']) {
		display: none !important;
	}

	/* ============================================
     FORM FIELD BLOCKS
     ============================================ */

	.dynamics-form-wrapper :global(.textFormFieldBlock),
	.dynamics-form-wrapper :global(.optionSetFormFieldBlock),
	.dynamics-form-wrapper :global(.phoneFormFieldBlock) {
		padding: 10px 0 !important;
		width: 100% !important;
		max-width: 100% !important;
		box-sizing: border-box !important;
	}

	/* Labels */
	.dynamics-form-wrapper :global(.textFormFieldBlock label),
	.dynamics-form-wrapper :global(.optionSetFormFieldBlock label),
	.dynamics-form-wrapper :global(.phoneFormFieldBlock label) {
		display: block !important;
		font-family: inherit !important;
		font-size: 14px !important;
		font-weight: 600 !important;
		color: #374151 !important;
		margin-bottom: 8px !important;
		width: 100% !important;
	}

	/* ============================================
     INPUTS - FORCE FULL WIDTH
     ============================================ */

	.dynamics-form-wrapper :global(input),
	.dynamics-form-wrapper :global(textarea),
	.dynamics-form-wrapper :global(select),
	.dynamics-form-wrapper :global(.textFormFieldBlock input),
	.dynamics-form-wrapper :global(.textFormFieldBlock textarea),
	.dynamics-form-wrapper :global(.optionSetFormFieldBlock select),
	.dynamics-form-wrapper :global(.phoneFormFieldBlock input) {
		width: 100% !important;
		max-width: 100% !important;
		min-width: 100% !important;
		padding: 14px 16px !important;
		background-color: #ffffff !important;
		border: 1px solid #e5e7eb !important;
		border-radius: 8px !important;
		font-size: 16px !important;
		color: #374151 !important;
		transition: all 0.2s ease !important;
		box-sizing: border-box !important;
		-webkit-appearance: none !important;
		appearance: none !important;
		display: block !important;
	}

	/* Focus state */
	.dynamics-form-wrapper :global(input:focus),
	.dynamics-form-wrapper :global(textarea:focus),
	.dynamics-form-wrapper :global(select:focus) {
		outline: none !important;
		border-color: #3b82f6 !important;
		box-shadow: 0 0 0 4px rgba(59, 130, 246, 0.1) !important;
	}

	/* Placeholder */
	.dynamics-form-wrapper :global(input::placeholder),
	.dynamics-form-wrapper :global(textarea::placeholder) {
		color: #9ca3af !important;
	}

	/* Textarea */
	.dynamics-form-wrapper :global(textarea) {
		min-height: 120px !important;
		resize: vertical !important;
	}

	/* Select dropdown */
	.dynamics-form-wrapper :global(select) {
		background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='none' viewBox='0 0 24 24' stroke='%239ca3af'%3E%3Cpath stroke-linecap='round' stroke-linejoin='round' stroke-width='2' d='M19 9l-7 7-7-7'%3E%3C/path%3E%3C/svg%3E") !important;
		background-repeat: no-repeat !important;
		background-position: right 12px center !important;
		background-size: 20px !important;
		padding-right: 40px !important;
		cursor: pointer !important;
	}

	/* ============================================
     SUBMIT BUTTON
     ============================================ */

	.dynamics-form-wrapper :global(.submitButtonWrapper),
	.dynamics-form-wrapper :global([data-editorblocktype='SubmitButton']) {
		padding: 20px 0 !important;
		text-align: right !important;
		width: 100% !important;
	}

	.dynamics-form-wrapper :global(.submitButton) {
		background-color: #1e40af !important;
		color: #ffffff !important;
		font-weight: 600 !important;
		font-size: 14px !important;
		letter-spacing: 0.05em !important;
		padding: 14px 48px !important;
		border: none !important;
		border-radius: 8px !important;
		cursor: pointer !important;
		transition: all 0.2s ease !important;
	}

	.dynamics-form-wrapper :global(.submitButton:hover) {
		background-color: #1e3a8a !important;
	}

	.dynamics-form-wrapper :global(.submitButton:active) {
		transform: scale(0.98) !important;
	}

	/* ============================================
     MOBILE RESPONSIVE
     ============================================ */

	@media screen and (max-width: 768px) {
		.dynamics-form-wrapper :global(.textFormFieldBlock),
		.dynamics-form-wrapper :global(.optionSetFormFieldBlock),
		.dynamics-form-wrapper :global(.phoneFormFieldBlock) {
			padding: 8px 0 !important;
		}

		.dynamics-form-wrapper :global(input),
		.dynamics-form-wrapper :global(textarea),
		.dynamics-form-wrapper :global(select) {
			padding: 12px 14px !important;
			font-size: 16px !important;
		}

		.dynamics-form-wrapper :global(.submitButtonWrapper),
		.dynamics-form-wrapper :global([data-editorblocktype='SubmitButton']) {
			text-align: center !important;
			padding: 16px 0 !important;
		}

		.dynamics-form-wrapper :global(.submitButton) {
			width: 100% !important;
			padding: 14px 24px !important;
		}
	}
</style>
