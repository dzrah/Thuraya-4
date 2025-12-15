<script>
	import { onMount } from 'svelte';
	import Section from './components/Section.svelte';
	import Container from './components/Container.svelte';

	onMount(() => {
		// Load the Dynamics 365 form script
		const script = document.createElement('script');
		script.src =
			'https://cxppusa1formui01cdnsa01-endpoint.azureedge.net/uae/FormLoader/FormLoader.bundle.js';
		script.onload = () => {
			// Wait for form to render, then fix widths
			setTimeout(fixFormWidth, 1500);
			setTimeout(fixFormWidth, 3000); // Run again in case of slow load
		};
		document.body.appendChild(script);
	});

	function fixFormWidth() {
		const wrapper = document.querySelector('.dynamics-form-wrapper');
		if (!wrapper) return;

		// Remove all hardcoded width styles (Dynamics uses width: 600px)
		wrapper.querySelectorAll('[style*="width: 600"]').forEach((el) => {
			el.style.width = '100%';
			el.style.maxWidth = '100%';
		});

		wrapper.querySelectorAll('[style*="width:600"]').forEach((el) => {
			el.style.width = '100%';
			el.style.maxWidth = '100%';
		});

		wrapper.querySelectorAll('.outer').forEach((el) => {
			el.style.width = '100%';
			el.style.maxWidth = '100%';
			el.style.display = 'block';
		});

		wrapper.querySelectorAll('table').forEach((el) => {
			el.style.width = '100%';
			el.style.maxWidth = '100%';
			el.style.tableLayout = 'fixed';
		});

		wrapper.querySelectorAll('th, td').forEach((el) => {
			el.style.width = '100%';
			el.style.display = 'block';
		});

		wrapper.querySelectorAll('.columnContainer').forEach((el) => {
			el.style.width = '100%';
		});

		// Remove width attributes
		wrapper.querySelectorAll('[width]').forEach((el) => {
			el.removeAttribute('width');
		});
	}
</script>

<Section bgClass="bg-[#f0f1f7]">
	<Container>
		<!-- Wrapper div to control the layout -->
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
     MAIN LAYOUT - KEEPS EVERYTHING IN CONTAINER
     ============================================ */

	.form-section-wrapper {
		display: flex;
		flex-direction: column;
		width: 100%;
		gap: 2rem;
		padding: 6rem 0;
		overflow: hidden; /* Critical - prevents children from breaking out */
	}

	@media (min-width: 768px) {
		.form-section-wrapper {
			flex-direction: row;
			align-items: flex-start;
			gap: 3rem;
		}
	}

	/* Left side - text content */
	.form-text-side {
		width: 100%;
		flex-shrink: 0;
	}

	@media (min-width: 768px) {
		.form-text-side {
			width: 40%;
			padding-right: 1rem;
		}
	}

	/* Right side - form container */
	.form-container-side {
		width: 100%;
		min-width: 0; /* Critical for flexbox - prevents overflow */
		overflow: hidden; /* Contains the form */
	}

	@media (min-width: 768px) {
		.form-container-side {
			width: 60%;
		}
	}

	/* ============================================
     DYNAMICS FORM WRAPPER
     ============================================ */

	.dynamics-form-wrapper {
		width: 100% !important;
		max-width: 100% !important;
		min-width: 0 !important;
		overflow: hidden !important;
		box-sizing: border-box !important;
	}

	/* Force ALL children to respect container width */
	.dynamics-form-wrapper :global(*) {
		max-width: 100% !important;
		box-sizing: border-box !important;
	}

	/* Override Dynamics fixed width (600px) */
	.dynamics-form-wrapper :global([data-layout='true']) {
		max-width: 100% !important;
		width: 100% !important;
		margin: 0 !important;
		padding: 0 !important;
		box-sizing: border-box !important;
	}

	.dynamics-form-wrapper :global(.outer) {
		width: 100% !important;
		max-width: 100% !important;
		display: block !important;
		box-sizing: border-box !important;
	}

	/* Fix the table that has width: 600px hardcoded */
	.dynamics-form-wrapper :global(table) {
		width: 100% !important;
		max-width: 100% !important;
		table-layout: fixed !important;
		box-sizing: border-box !important;
	}

	.dynamics-form-wrapper :global(table[style*='600px']),
	.dynamics-form-wrapper :global(table[style*='600']),
	.dynamics-form-wrapper :global(table[width='600']) {
		width: 100% !important;
		max-width: 100% !important;
	}

	.dynamics-form-wrapper :global(th),
	.dynamics-form-wrapper :global(td) {
		width: 100% !important;
		display: block !important;
		box-sizing: border-box !important;
	}

	.dynamics-form-wrapper :global(.columnContainer) {
		width: 100% !important;
		max-width: 100% !important;
	}

	.dynamics-form-wrapper :global(.inner) {
		width: 100% !important;
		max-width: 100% !important;
		padding: 0 !important;
	}

	.dynamics-form-wrapper :global(.containerWrapper) {
		width: 100% !important;
		max-width: 100% !important;
	}

	.dynamics-form-wrapper :global(.tbContainer) {
		width: 100% !important;
		max-width: 100% !important;
	}

	/* ============================================
     FORM BASE STYLES
     ============================================ */

	.dynamics-form-wrapper :global(.marketingForm) {
		font-family: inherit !important;
		width: 100% !important;
		max-width: 100% !important;
	}

	/* Hide default headings from Dynamics */
	.dynamics-form-wrapper :global([data-editorblocktype='Text']) {
		display: none !important;
	}

	/* ============================================
     FORM FIELD BLOCKS
     ============================================ */

	.dynamics-form-wrapper :global(.textFormFieldBlock),
	.dynamics-form-wrapper :global(.optionSetFormFieldBlock),
	.dynamics-form-wrapper :global(.phoneFormFieldBlock) {
		padding: 8px 0 !important;
		gap: 8px !important;
		width: 100% !important;
		box-sizing: border-box !important;
	}

	/* Hide labels (using placeholders instead) */
	.dynamics-form-wrapper :global(.textFormFieldBlock label),
	.dynamics-form-wrapper :global(.optionSetFormFieldBlock label),
	.dynamics-form-wrapper :global(.optionSetFormFieldBlock label.block-label),
	.dynamics-form-wrapper :global(.phoneFormFieldBlock label) {
		display: none !important;
	}

	/* ============================================
     INPUT FIELDS
     ============================================ */

	.dynamics-form-wrapper :global(.textFormFieldBlock input),
	.dynamics-form-wrapper :global(.textFormFieldBlock textarea),
	.dynamics-form-wrapper :global(.optionSetFormFieldBlock select),
	.dynamics-form-wrapper :global(.phoneFormFieldBlock input) {
		width: 100% !important;
		max-width: 100% !important;
		padding: 16px 20px !important;
		background-color: #ffffff !important;
		border: 1px solid #e5e7eb !important;
		border-radius: 8px !important;
		font-size: 16px !important; /* Prevents iOS zoom on focus */
		color: #374151 !important;
		transition: all 0.2s ease !important;
		box-sizing: border-box !important;
		-webkit-appearance: none !important;
		appearance: none !important;
	}

	/* Focus state */
	.dynamics-form-wrapper :global(.textFormFieldBlock input:focus),
	.dynamics-form-wrapper :global(.textFormFieldBlock textarea:focus),
	.dynamics-form-wrapper :global(.optionSetFormFieldBlock select:focus),
	.dynamics-form-wrapper :global(.phoneFormFieldBlock input:focus) {
		outline: none !important;
		border-color: #3b82f6 !important;
		box-shadow: 0 0 0 4px rgba(59, 130, 246, 0.1) !important;
	}

	/* Placeholder text */
	.dynamics-form-wrapper :global(input::placeholder),
	.dynamics-form-wrapper :global(textarea::placeholder) {
		color: #9ca3af !important;
	}

	/* Textarea specific */
	.dynamics-form-wrapper :global(.textFormFieldBlock textarea) {
		min-height: 120px !important;
		resize: none !important;
	}

	/* ============================================
     SELECT DROPDOWN
     ============================================ */

	.dynamics-form-wrapper :global(.optionSetFormFieldBlock select) {
		background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='none' viewBox='0 0 24 24' stroke='%239ca3af'%3E%3Cpath stroke-linecap='round' stroke-linejoin='round' stroke-width='2' d='M19 9l-7 7-7-7'%3E%3C/path%3E%3C/svg%3E") !important;
		background-repeat: no-repeat !important;
		background-position: right 12px center !important;
		background-size: 20px !important;
		padding-right: 40px !important;
		cursor: pointer !important;
	}

	/* ============================================
     PHONE FIELD
     ============================================ */

	.dynamics-form-wrapper :global(.phoneCountryCode) {
		border-radius: 8px !important;
		overflow: hidden !important;
		width: 100% !important;
	}

	.dynamics-form-wrapper :global(.phoneCountryCodeLabel) {
		background-color: #f3f4f6 !important;
		padding: 16px 12px !important;
	}

	/* ============================================
     SUBMIT BUTTON
     ============================================ */

	.dynamics-form-wrapper :global(.submitButtonWrapper),
	.dynamics-form-wrapper :global([data-editorblocktype='SubmitButton']) {
		text-align: right !important;
		padding: 16px 0 !important;
		margin-top: 8px !important;
		width: 100% !important;
	}

	.dynamics-form-wrapper :global(.submitButton) {
		background-color: #1e40af !important;
		color: #ffffff !important;
		font-weight: 600 !important;
		font-size: 14px !important;
		letter-spacing: 0.05em !important;
		padding: 16px 56px !important;
		border: none !important;
		border-radius: 8px !important;
		cursor: pointer !important;
		transition: all 0.2s ease !important;
		-webkit-appearance: none !important;
	}

	.dynamics-form-wrapper :global(.submitButton:hover) {
		background-color: #1e3a8a !important;
	}

	.dynamics-form-wrapper :global(.submitButton:active) {
		transform: scale(0.98) !important;
	}

	/* ============================================
     ERROR MESSAGES
     ============================================ */

	.dynamics-form-wrapper :global(.error) {
		color: #dc2626 !important;
		font-size: 0.85rem !important;
		margin-top: 4px !important;
	}

	/* Domain error message styling */
	.dynamics-form-wrapper :global(.notification-message),
	.dynamics-form-wrapper :global([class*='error']) {
		width: 100% !important;
		max-width: 100% !important;
		word-wrap: break-word !important;
		white-space: normal !important;
	}

	/* ============================================
     MOBILE RESPONSIVE STYLES
     ============================================ */

	@media screen and (max-width: 768px) {
		/* Force full width on everything */
		.dynamics-form-wrapper :global(*) {
			max-width: 100% !important;
		}

		.dynamics-form-wrapper :global([data-layout='true']) {
			padding: 0 !important;
		}

		.dynamics-form-wrapper :global(.outer) {
			width: 100% !important;
		}

		.dynamics-form-wrapper :global(th),
		.dynamics-form-wrapper :global(td),
		.dynamics-form-wrapper :global(.columnContainer),
		.dynamics-form-wrapper :global(.inner) {
			width: 100% !important;
			padding-left: 0 !important;
			padding-right: 0 !important;
		}

		/* Form field blocks */
		.dynamics-form-wrapper :global(.textFormFieldBlock),
		.dynamics-form-wrapper :global(.optionSetFormFieldBlock),
		.dynamics-form-wrapper :global(.phoneFormFieldBlock) {
			padding: 6px 0 !important;
		}

		/* Larger touch targets on mobile */
		.dynamics-form-wrapper :global(.textFormFieldBlock input),
		.dynamics-form-wrapper :global(.textFormFieldBlock textarea),
		.dynamics-form-wrapper :global(.optionSetFormFieldBlock select),
		.dynamics-form-wrapper :global(.phoneFormFieldBlock input) {
			padding: 14px 16px !important;
			font-size: 16px !important;
			min-height: 50px !important;
		}

		/* Full width button on mobile */
		.dynamics-form-wrapper :global(.submitButtonWrapper),
		.dynamics-form-wrapper :global([data-editorblocktype='SubmitButton']) {
			text-align: center !important;
			padding: 12px 0 !important;
		}

		.dynamics-form-wrapper :global(.submitButton) {
			width: 100% !important;
			padding: 16px 24px !important;
			font-size: 14px !important;
		}
	}

	/* ============================================
     SMALL MOBILE (< 480px)
     ============================================ */

	@media screen and (max-width: 480px) {
		.dynamics-form-wrapper :global(.textFormFieldBlock input),
		.dynamics-form-wrapper :global(.textFormFieldBlock textarea),
		.dynamics-form-wrapper :global(.optionSetFormFieldBlock select),
		.dynamics-form-wrapper :global(.phoneFormFieldBlock input) {
			padding: 12px 14px !important;
			border-radius: 6px !important;
		}

		.dynamics-form-wrapper :global(.textFormFieldBlock textarea) {
			min-height: 100px !important;
		}

		.dynamics-form-wrapper :global(.submitButton) {
			padding: 14px 20px !important;
			border-radius: 6px !important;
		}
	}
</style>
