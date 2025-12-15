<script>
	import Container from './Container.svelte';
	import Section from './Section.svelte';

	// ============================================
	// PREVIEW MODE FLAG
	// Set to false when you're ready to use the real Dynamics form
	// ============================================
	const PREVIEW_MODE = true;

	// ============================================
	// STATE (for preview mode)
	// ============================================
	let formData = $state({
		firstName: '',
		lastName: '',
		email: '',
		phone: '',
		company: '',
		jobTitle: '',
		description: ''
	});

	let isSubmitting = $state(false);
	let submitSuccess = $state(false);

	// Preview submit handler
	async function handlePreviewSubmit(e) {
		e.preventDefault();
		isSubmitting = true;

		// Simulate API call
		await new Promise((resolve) => setTimeout(resolve, 1500));

		console.log('Form data (preview):', formData);
		submitSuccess = true;
		isSubmitting = false;

		// Reset after 3 seconds
		setTimeout(() => {
			submitSuccess = false;
		}, 3000);
	}

	// ============================================
	// REAL DYNAMICS FORM LOADER (when not in preview)
	// ============================================
	import { onMount } from 'svelte';

	onMount(() => {
		if (!PREVIEW_MODE) {
			const script = document.createElement('script');
			script.src =
				'https://cxppusa1formui01cdnsa01-endpoint.azureedge.net/uae/FormLoader/FormLoader.bundle.js';
			script.onload = () => {
				setTimeout(fixFormWidth, 1500);
				setTimeout(fixFormWidth, 3000);
			};
			document.body.appendChild(script);
		}
	});

	function fixFormWidth() {
		const wrapper = document.querySelector('.dynamics-form-wrapper');
		if (!wrapper) return;

		wrapper.querySelectorAll('[style*="width: 600"]').forEach((el) => {
			el.style.width = '100%';
			el.style.maxWidth = '100%';
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
	}
</script>

<Section bgClass="bg-[#f0f1f7]">
	<Container>
		<div class="form-layout">
			<!-- Left side: Text content -->
			<div class="form-text-content">
				<h2 class="form-title">Start Your Thuraya-4 Deployment</h2>
				<p class="form-subtitle">Speak with a specialist on products, services, and timelines</p>
				<p class="form-mandatory">* Mandatory Field</p>

				{#if PREVIEW_MODE}
					<div class="preview-badge">⚠️ Preview Mode — Form submissions are simulated</div>
				{/if}
			</div>

			<!-- Right side: Form -->
			<div class="form-container">
				{#if PREVIEW_MODE}
					<!-- ============================================
               PREVIEW FORM
               ============================================ -->
					<form onsubmit={handlePreviewSubmit} class="preview-form">
						{#if submitSuccess}
							<div class="success-message">
								<p class="success-title">Thank you for your message!</p>
								<p class="success-text">We'll get back to you shortly.</p>
							</div>
						{/if}

						<!-- First Name -->
						<div class="form-field">
							<input
								type="text"
								placeholder="First Name *"
								bind:value={formData.firstName}
								required
								class="form-input"
							/>
						</div>

						<!-- Last Name -->
						<div class="form-field">
							<input
								type="text"
								placeholder="Last Name *"
								bind:value={formData.lastName}
								required
								class="form-input"
							/>
						</div>

						<!-- Email -->
						<div class="form-field">
							<input
								type="email"
								placeholder="Email *"
								bind:value={formData.email}
								required
								class="form-input"
							/>
						</div>

						<!-- Phone -->
						<div class="form-field">
							<input
								type="tel"
								placeholder="Phone Number *"
								bind:value={formData.phone}
								required
								class="form-input"
							/>
						</div>

						<!-- Company Name -->
						<div class="form-field">
							<input
								type="text"
								placeholder="Company Name"
								bind:value={formData.company}
								class="form-input"
							/>
						</div>

						<!-- Job Title -->
						<div class="form-field">
							<input
								type="text"
								placeholder="Job Title"
								bind:value={formData.jobTitle}
								class="form-input"
							/>
						</div>

						<!-- Description / Message -->
						<div class="form-field">
							<textarea
								placeholder="Description"
								bind:value={formData.description}
								rows="5"
								class="form-input form-textarea"
							></textarea>
						</div>

						<!-- Submit Button -->
						<div class="form-submit">
							<button type="submit" disabled={isSubmitting} class="submit-button">
								{#if isSubmitting}
									<span class="submit-loading">
										<svg class="spinner" viewBox="0 0 24 24">
											<circle
												class="spinner-bg"
												cx="12"
												cy="12"
												r="10"
												stroke="currentColor"
												stroke-width="4"
												fill="none"
											/>
											<path
												class="spinner-fg"
												fill="currentColor"
												d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"
											/>
										</svg>
										Submitting...
									</span>
								{:else}
									Submit
								{/if}
							</button>
						</div>
					</form>
				{:else}
					<!-- ============================================
               REAL DYNAMICS FORM
               ============================================ -->
					<div class="dynamics-form-wrapper">
						<div
							data-form-id="92e5516c-d6af-f011-bbd3-6045bd6abf1b"
							data-form-api-url="https://public-uae.mkt.dynamics.com/api/v1.0/orgs/b0843b43-2e40-ee11-94d3-6045bd6a6257/landingpageforms"
							data-cached-form-url="https://assets-uae.mkt.dynamics.com/b0843b43-2e40-ee11-94d3-6045bd6a6257/digitalassets/forms/92e5516c-d6af-f011-bbd3-6045bd6abf1b"
						></div>
					</div>
				{/if}
			</div>
		</div>
	</Container>
</Section>

<style>
	/* ============================================
     MAIN LAYOUT
     ============================================ */

	.form-layout {
		display: flex;
		flex-direction: column;
		gap: 2rem;
		width: 100%;
		padding: 4rem 0;
	}

	@media (min-width: 768px) {
		.form-layout {
			flex-direction: row;
			align-items: flex-start;
			gap: 3rem;
		}
	}

	/* ============================================
     LEFT SIDE - TEXT CONTENT
     ============================================ */

	.form-text-content {
		width: 100%;
		flex-shrink: 0;
	}

	@media (min-width: 768px) {
		.form-text-content {
			width: 40%;
			padding-right: 1rem;
		}
	}

	.form-title {
		color: #0e329b;
		font-weight: 600;
		font-size: 1.5rem;
		line-height: 1.3;
		margin-bottom: 1rem;
		text-align: center;
	}

	@media (min-width: 640px) {
		.form-title {
			font-size: 1.7rem;
			text-align: left;
		}
	}

	.form-subtitle {
		font-weight: 300;
		font-size: 1rem;
		color: #666666;
		margin-bottom: 2rem;
		text-align: center;
	}

	@media (min-width: 640px) {
		.form-subtitle {
			font-size: 1.2rem;
			text-align: left;
		}
	}

	.form-mandatory {
		font-weight: 300;
		font-size: 0.75rem;
		color: #666666;
		text-align: center;
	}

	@media (min-width: 640px) {
		.form-mandatory {
			text-align: left;
		}
	}

	.preview-badge {
		display: none;
		margin-top: 1.5rem;
		padding: 0.5rem 0.75rem;
		background-color: #fef3c7;
		border: 1px solid #fcd34d;
		border-radius: 0.5rem;
		color: #92400e;
		font-size: 0.75rem;
	}

	@media (min-width: 640px) {
		.preview-badge {
			display: block;
		}
	}

	/* ============================================
     RIGHT SIDE - FORM CONTAINER
     ============================================ */

	.form-container {
		width: 100%;
		min-width: 0; /* Critical for flexbox overflow */
		overflow: hidden; /* Contain the form */
	}

	@media (min-width: 768px) {
		.form-container {
			width: 60%;
		}
	}

	/* ============================================
     PREVIEW FORM STYLES
     ============================================ */

	.preview-form {
		width: 100%;
	}

	.form-field {
		margin-bottom: 1rem;
	}

	.form-input {
		width: 100%;
		padding: 1rem 1.25rem;
		background-color: #ffffff;
		border: 1px solid #e5e7eb;
		border-radius: 0.5rem;
		font-size: 1rem;
		color: #374151;
		transition: all 0.2s ease;
		box-sizing: border-box;
		-webkit-appearance: none;
		appearance: none;
	}

	.form-input:focus {
		outline: none;
		border-color: #3b82f6;
		box-shadow: 0 0 0 4px rgba(59, 130, 246, 0.1);
	}

	.form-input::placeholder {
		color: #9ca3af;
	}

	.form-textarea {
		min-height: 120px;
		resize: none;
	}

	.form-submit {
		text-align: center;
		margin-top: 1.5rem;
	}

	@media (min-width: 640px) {
		.form-submit {
			text-align: right;
		}
	}

	.submit-button {
		background-color: #1e40af;
		color: #ffffff;
		font-weight: 600;
		font-size: 0.875rem;
		letter-spacing: 0.05em;
		padding: 1rem 3.5rem;
		border: none;
		border-radius: 0.5rem;
		cursor: pointer;
		transition: all 0.2s ease;
		width: 100%;
	}

	@media (min-width: 640px) {
		.submit-button {
			width: auto;
		}
	}

	.submit-button:hover {
		background-color: #1e3a8a;
	}

	.submit-button:active {
		transform: scale(0.98);
	}

	.submit-button:disabled {
		opacity: 0.6;
		cursor: not-allowed;
	}

	.submit-loading {
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 0.5rem;
	}

	.spinner {
		width: 1.25rem;
		height: 1.25rem;
		animation: spin 1s linear infinite;
	}

	.spinner-bg {
		opacity: 0.25;
	}

	.spinner-fg {
		opacity: 0.75;
	}

	@keyframes spin {
		from {
			transform: rotate(0deg);
		}
		to {
			transform: rotate(360deg);
		}
	}

	/* Success Message */
	.success-message {
		background-color: #f0fdf4;
		border: 1px solid #bbf7d0;
		color: #166534;
		padding: 1rem 1.5rem;
		border-radius: 0.5rem;
		margin-bottom: 1.5rem;
	}

	.success-title {
		font-weight: 500;
	}

	.success-text {
		font-size: 0.875rem;
		margin-top: 0.25rem;
	}

	/* ============================================
     DYNAMICS FORM WRAPPER & OVERRIDES
     ============================================ */

	.dynamics-form-wrapper {
		width: 100% !important;
		max-width: 100% !important;
		min-width: 0 !important;
		overflow: hidden !important;
		box-sizing: border-box !important;
	}

	/* Force all Dynamics elements to stay within container */
	.dynamics-form-wrapper :global(*) {
		max-width: 100% !important;
		box-sizing: border-box !important;
	}

	.dynamics-form-wrapper :global([data-layout='true']) {
		max-width: 100% !important;
		width: 100% !important;
		margin: 0 !important;
		padding: 0 !important;
	}

	.dynamics-form-wrapper :global(.outer),
	.dynamics-form-wrapper :global(table) {
		width: 100% !important;
		max-width: 100% !important;
		table-layout: fixed !important;
		display: block !important;
	}

	.dynamics-form-wrapper :global(th),
	.dynamics-form-wrapper :global(td),
	.dynamics-form-wrapper :global(.columnContainer),
	.dynamics-form-wrapper :global(.inner) {
		width: 100% !important;
		max-width: 100% !important;
		display: block !important;
		padding-left: 0 !important;
		padding-right: 0 !important;
	}

	/* Hide Dynamics default headings */
	.dynamics-form-wrapper :global([data-editorblocktype='Text']) {
		display: none !important;
	}

	/* Hide labels */
	.dynamics-form-wrapper :global(.textFormFieldBlock label),
	.dynamics-form-wrapper :global(.optionSetFormFieldBlock label),
	.dynamics-form-wrapper :global(.phoneFormFieldBlock label) {
		display: none !important;
	}

	/* Style inputs */
	.dynamics-form-wrapper :global(.textFormFieldBlock input),
	.dynamics-form-wrapper :global(.textFormFieldBlock textarea),
	.dynamics-form-wrapper :global(.optionSetFormFieldBlock select),
	.dynamics-form-wrapper :global(.phoneFormFieldBlock input) {
		width: 100% !important;
		max-width: 100% !important;
		padding: 1rem 1.25rem !important;
		background-color: #ffffff !important;
		border: 1px solid #e5e7eb !important;
		border-radius: 0.5rem !important;
		font-size: 1rem !important;
		color: #374151 !important;
		transition: all 0.2s ease !important;
		box-sizing: border-box !important;
	}

	.dynamics-form-wrapper :global(.textFormFieldBlock input:focus),
	.dynamics-form-wrapper :global(.textFormFieldBlock textarea:focus),
	.dynamics-form-wrapper :global(.optionSetFormFieldBlock select:focus) {
		outline: none !important;
		border-color: #3b82f6 !important;
		box-shadow: 0 0 0 4px rgba(59, 130, 246, 0.1) !important;
	}

	.dynamics-form-wrapper :global(.textFormFieldBlock textarea) {
		min-height: 120px !important;
		resize: none !important;
	}

	/* Submit button */
	.dynamics-form-wrapper :global(.submitButtonWrapper),
	.dynamics-form-wrapper :global([data-editorblocktype='SubmitButton']) {
		text-align: right !important;
		padding: 1rem 0 !important;
	}

	.dynamics-form-wrapper :global(.submitButton) {
		background-color: #1e40af !important;
		color: #ffffff !important;
		font-weight: 600 !important;
		font-size: 0.875rem !important;
		padding: 1rem 3.5rem !important;
		border: none !important;
		border-radius: 0.5rem !important;
		cursor: pointer !important;
		transition: all 0.2s ease !important;
	}

	.dynamics-form-wrapper :global(.submitButton:hover) {
		background-color: #1e3a8a !important;
	}

	/* Mobile styles for Dynamics form */
	@media screen and (max-width: 640px) {
		.dynamics-form-wrapper :global(.submitButtonWrapper),
		.dynamics-form-wrapper :global([data-editorblocktype='SubmitButton']) {
			text-align: center !important;
		}

		.dynamics-form-wrapper :global(.submitButton) {
			width: 100% !important;
		}
	}
</style>
