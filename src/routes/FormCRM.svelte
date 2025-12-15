<script>
	import { onMount } from 'svelte';
	import Section from './components/Section.svelte';
	import Container from './components/Container.svelte';

	onMount(() => {
		// Load the Dynamics form script
		const script = document.createElement('script');
		script.src =
			'https://cxppusa1formui01cdnsa01-endpoint.azureedge.net/uae/FormLoader/FormLoader.bundle.js';
		document.body.appendChild(script);
	});
</script>

<Section bgClass="bg-[#f0f1f7]">
	<Container class="md:flex md:flex-row items-start justify-center py-25 w-full flex-col">
		<!-- Left side: Your text content -->
		<div class="flex-col items-start justify-center w-full">
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
		<div class="w-full dynamics-form-wrapper">
			<div
				data-form-id="92e5516c-d6af-f011-bbd3-6045bd6abf1b"
				data-form-api-url="https://public-uae.mkt.dynamics.com/api/v1.0/orgs/b0843b43-2e40-ee11-94d3-6045bd6a6257/landingpageforms"
				data-cached-form-url="https://assets-uae.mkt.dynamics.com/b0843b43-2e40-ee11-94d3-6045bd6a6257/digitalassets/forms/92e5516c-d6af-f011-bbd3-6045bd6abf1b"
			></div>
		</div>
	</Container>
</Section>

<style>
	/* ============================================
     OVERRIDE DYNAMICS 365 FORM STYLES
     ============================================ */

	/* Form container */
	.dynamics-form-wrapper :global(.marketingForm) {
		font-family: inherit;
	}

	.dynamics-form-wrapper :global([data-layout='true']) {
		max-width: 100% !important;
		background-color: transparent !important;
	}

	/* Hide default headings from Dynamics (we have our own) */
	.dynamics-form-wrapper :global(.marketingForm h1),
	.dynamics-form-wrapper :global(.marketingForm h2),
	.dynamics-form-wrapper :global(.marketingForm p:first-of-type) {
		display: none !important;
	}

	/* Field blocks */
	.dynamics-form-wrapper :global(.textFormFieldBlock),
	.dynamics-form-wrapper :global(.optionSetFormFieldBlock),
	.dynamics-form-wrapper :global(.phoneFormFieldBlock) {
		padding: 8px 0 !important;
		gap: 8px !important;
	}

	/* Labels */
	.dynamics-form-wrapper :global(.textFormFieldBlock label),
	.dynamics-form-wrapper :global(.optionSetFormFieldBlock label),
	.dynamics-form-wrapper :global(.phoneFormFieldBlock label) {
		display: none !important; /* Hide labels, use placeholders instead */
	}

	/* Show labels if you prefer */
	/*
  .dynamics-form-wrapper :global(.textFormFieldBlock label) {
    font-family: inherit !important;
    font-size: 0.9rem !important;
    font-weight: 500 !important;
    color: #374151 !important;
    margin-bottom: 4px !important;
  }
  */

	/* Input fields */
	.dynamics-form-wrapper :global(.textFormFieldBlock input),
	.dynamics-form-wrapper :global(.textFormFieldBlock textarea),
	.dynamics-form-wrapper :global(.optionSetFormFieldBlock select),
	.dynamics-form-wrapper :global(.phoneFormFieldBlock input) {
		width: 100% !important;
		padding: 16px 20px !important;
		background-color: #ffffff !important;
		border: 1px solid #e5e7eb !important;
		border-radius: 8px !important;
		font-size: 0.95rem !important;
		color: #374151 !important;
		transition: all 0.2s ease !important;
	}

	/* Input focus state */
	.dynamics-form-wrapper :global(.textFormFieldBlock input:focus),
	.dynamics-form-wrapper :global(.textFormFieldBlock textarea:focus),
	.dynamics-form-wrapper :global(.optionSetFormFieldBlock select:focus),
	.dynamics-form-wrapper :global(.phoneFormFieldBlock input:focus) {
		outline: none !important;
		border-color: #3b82f6 !important;
		box-shadow: 0 0 0 4px rgba(59, 130, 246, 0.1) !important;
	}

	/* Placeholder text */
	.dynamics-form-wrapper :global(.textFormFieldBlock input::placeholder),
	.dynamics-form-wrapper :global(.textFormFieldBlock textarea::placeholder) {
		color: #9ca3af !important;
	}

	/* Textarea */
	.dynamics-form-wrapper :global(.textFormFieldBlock textarea) {
		min-height: 120px !important;
		resize: none !important;
	}

	/* Select dropdown */
	.dynamics-form-wrapper :global(.optionSetFormFieldBlock select) {
		appearance: none !important;
		background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' fill='none' viewBox='0 0 24 24' stroke='%239ca3af'%3E%3Cpath stroke-linecap='round' stroke-linejoin='round' stroke-width='2' d='M19 9l-7 7-7-7'%3E%3C/path%3E%3C/svg%3E") !important;
		background-repeat: no-repeat !important;
		background-position: right 12px center !important;
		background-size: 20px !important;
		padding-right: 40px !important;
		cursor: pointer !important;
	}

	/* Submit button wrapper */
	.dynamics-form-wrapper :global(.submitButtonWrapper),
	.dynamics-form-wrapper :global([data-editorblocktype='SubmitButton']) {
		text-align: right !important;
		padding: 16px 0 !important;
		margin-top: 8px !important;
	}

	/* Submit button */
	.dynamics-form-wrapper :global(.submitButton) {
		background-color: #1e40af !important;
		color: #ffffff !important;
		font-weight: 600 !important;
		font-size: 0.9rem !important;
		letter-spacing: 0.05em !important;
		padding: 16px 56px !important;
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

	/* Error messages */
	.dynamics-form-wrapper :global(.error) {
		color: #dc2626 !important;
		font-size: 0.85rem !important;
		margin-top: 4px !important;
	}

	/* Hide any unwanted sections */
	.dynamics-form-wrapper :global([data-editorblocktype='Text']) {
		display: none !important;
	}

	/* Phone field special handling */
	.dynamics-form-wrapper :global(.phoneCountryCode) {
		border-radius: 8px !important;
		overflow: hidden !important;
	}

	.dynamics-form-wrapper :global(.phoneCountryCodeLabel) {
		background-color: #f3f4f6 !important;
		padding: 16px 12px !important;
	}
</style>
