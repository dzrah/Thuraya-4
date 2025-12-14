<!-- <script>
	import Container from './Container.svelte';
	import Section from './Section.svelte';

	let formData = $state({
		firstName: '',
		lastName: '',
		company: '',
		email: '',
		phone: '',
		country: '',
		message: ''
	});

	let errors = $state({});
	let isSubmitting = $state(false);
	let submitSuccess = $state(false);

	const countries = [
		{ code: 'AF', name: 'Afghanistan' },
		{ code: 'AL', name: 'Albania' },
		{ code: 'DZ', name: 'Algeria' },
		{ code: 'AD', name: 'Andorra' },
		{ code: 'AO', name: 'Angola' },
		{ code: 'AG', name: 'Antigua and Barbuda' },
		{ code: 'AR', name: 'Argentina' },
		{ code: 'AM', name: 'Armenia' },
		{ code: 'AU', name: 'Australia' },
		{ code: 'AT', name: 'Austria' },
		{ code: 'AZ', name: 'Azerbaijan' },
		{ code: 'BS', name: 'Bahamas' },
		{ code: 'BH', name: 'Bahrain' },
		{ code: 'BD', name: 'Bangladesh' },
		{ code: 'BB', name: 'Barbados' },
		{ code: 'BY', name: 'Belarus' },
		{ code: 'BE', name: 'Belgium' },
		{ code: 'BZ', name: 'Belize' },
		{ code: 'BJ', name: 'Benin' },
		{ code: 'BT', name: 'Bhutan' },
		{ code: 'BO', name: 'Bolivia' },
		{ code: 'BA', name: 'Bosnia and Herzegovina' },
		{ code: 'BW', name: 'Botswana' },
		{ code: 'BR', name: 'Brazil' },
		{ code: 'BN', name: 'Brunei' },
		{ code: 'BG', name: 'Bulgaria' },
		{ code: 'BF', name: 'Burkina Faso' },
		{ code: 'BI', name: 'Burundi' },
		{ code: 'CV', name: 'Cabo Verde' },
		{ code: 'KH', name: 'Cambodia' },
		{ code: 'CM', name: 'Cameroon' },
		{ code: 'CA', name: 'Canada' },
		{ code: 'CF', name: 'Central African Republic' },
		{ code: 'TD', name: 'Chad' },
		{ code: 'CL', name: 'Chile' },
		{ code: 'CN', name: 'China' },
		{ code: 'CO', name: 'Colombia' },
		{ code: 'KM', name: 'Comoros' },
		{ code: 'CG', name: 'Congo' },
		{ code: 'CD', name: 'Congo (Democratic Republic)' },
		{ code: 'CR', name: 'Costa Rica' },
		{ code: 'CI', name: "Côte d'Ivoire" },
		{ code: 'HR', name: 'Croatia' },
		{ code: 'CU', name: 'Cuba' },
		{ code: 'CY', name: 'Cyprus' },
		{ code: 'CZ', name: 'Czech Republic' },
		{ code: 'DK', name: 'Denmark' },
		{ code: 'DJ', name: 'Djibouti' },
		{ code: 'DM', name: 'Dominica' },
		{ code: 'DO', name: 'Dominican Republic' },
		{ code: 'EC', name: 'Ecuador' },
		{ code: 'EG', name: 'Egypt' },
		{ code: 'SV', name: 'El Salvador' },
		{ code: 'GQ', name: 'Equatorial Guinea' },
		{ code: 'ER', name: 'Eritrea' },
		{ code: 'EE', name: 'Estonia' },
		{ code: 'SZ', name: 'Eswatini' },
		{ code: 'ET', name: 'Ethiopia' },
		{ code: 'FJ', name: 'Fiji' },
		{ code: 'FI', name: 'Finland' },
		{ code: 'FR', name: 'France' },
		{ code: 'GA', name: 'Gabon' },
		{ code: 'GM', name: 'Gambia' },
		{ code: 'GE', name: 'Georgia' },
		{ code: 'DE', name: 'Germany' },
		{ code: 'GH', name: 'Ghana' },
		{ code: 'GR', name: 'Greece' },
		{ code: 'GD', name: 'Grenada' },
		{ code: 'GT', name: 'Guatemala' },
		{ code: 'GN', name: 'Guinea' },
		{ code: 'GW', name: 'Guinea-Bissau' },
		{ code: 'GY', name: 'Guyana' },
		{ code: 'HT', name: 'Haiti' },
		{ code: 'HN', name: 'Honduras' },
		{ code: 'HU', name: 'Hungary' },
		{ code: 'IS', name: 'Iceland' },
		{ code: 'IN', name: 'India' },
		{ code: 'ID', name: 'Indonesia' },
		{ code: 'IR', name: 'Iran' },
		{ code: 'IQ', name: 'Iraq' },
		{ code: 'IE', name: 'Ireland' },
		{ code: 'IL', name: 'Israel' },
		{ code: 'IT', name: 'Italy' },
		{ code: 'JM', name: 'Jamaica' },
		{ code: 'JP', name: 'Japan' },
		{ code: 'JO', name: 'Jordan' },
		{ code: 'KZ', name: 'Kazakhstan' },
		{ code: 'KE', name: 'Kenya' },
		{ code: 'KI', name: 'Kiribati' },
		{ code: 'KP', name: 'Korea (North)' },
		{ code: 'KR', name: 'Korea (South)' },
		{ code: 'KW', name: 'Kuwait' },
		{ code: 'KG', name: 'Kyrgyzstan' },
		{ code: 'LA', name: 'Laos' },
		{ code: 'LV', name: 'Latvia' },
		{ code: 'LB', name: 'Lebanon' },
		{ code: 'LS', name: 'Lesotho' },
		{ code: 'LR', name: 'Liberia' },
		{ code: 'LY', name: 'Libya' },
		{ code: 'LI', name: 'Liechtenstein' },
		{ code: 'LT', name: 'Lithuania' },
		{ code: 'LU', name: 'Luxembourg' },
		{ code: 'MG', name: 'Madagascar' },
		{ code: 'MW', name: 'Malawi' },
		{ code: 'MY', name: 'Malaysia' },
		{ code: 'MV', name: 'Maldives' },
		{ code: 'ML', name: 'Mali' },
		{ code: 'MT', name: 'Malta' },
		{ code: 'MH', name: 'Marshall Islands' },
		{ code: 'MR', name: 'Mauritania' },
		{ code: 'MU', name: 'Mauritius' },
		{ code: 'MX', name: 'Mexico' },
		{ code: 'FM', name: 'Micronesia' },
		{ code: 'MD', name: 'Moldova' },
		{ code: 'MC', name: 'Monaco' },
		{ code: 'MN', name: 'Mongolia' },
		{ code: 'ME', name: 'Montenegro' },
		{ code: 'MA', name: 'Morocco' },
		{ code: 'MZ', name: 'Mozambique' },
		{ code: 'MM', name: 'Myanmar' },
		{ code: 'NA', name: 'Namibia' },
		{ code: 'NR', name: 'Nauru' },
		{ code: 'NP', name: 'Nepal' },
		{ code: 'NL', name: 'Netherlands' },
		{ code: 'NZ', name: 'New Zealand' },
		{ code: 'NI', name: 'Nicaragua' },
		{ code: 'NE', name: 'Niger' },
		{ code: 'NG', name: 'Nigeria' },
		{ code: 'MK', name: 'North Macedonia' },
		{ code: 'NO', name: 'Norway' },
		{ code: 'OM', name: 'Oman' },
		{ code: 'PK', name: 'Pakistan' },
		{ code: 'PW', name: 'Palau' },
		{ code: 'PS', name: 'Palestine' },
		{ code: 'PA', name: 'Panama' },
		{ code: 'PG', name: 'Papua New Guinea' },
		{ code: 'PY', name: 'Paraguay' },
		{ code: 'PE', name: 'Peru' },
		{ code: 'PH', name: 'Philippines' },
		{ code: 'PL', name: 'Poland' },
		{ code: 'PT', name: 'Portugal' },
		{ code: 'QA', name: 'Qatar' },
		{ code: 'RO', name: 'Romania' },
		{ code: 'RU', name: 'Russia' },
		{ code: 'RW', name: 'Rwanda' },
		{ code: 'KN', name: 'Saint Kitts and Nevis' },
		{ code: 'LC', name: 'Saint Lucia' },
		{ code: 'VC', name: 'Saint Vincent and the Grenadines' },
		{ code: 'WS', name: 'Samoa' },
		{ code: 'SM', name: 'San Marino' },
		{ code: 'ST', name: 'Sao Tome and Principe' },
		{ code: 'SA', name: 'Saudi Arabia' },
		{ code: 'SN', name: 'Senegal' },
		{ code: 'RS', name: 'Serbia' },
		{ code: 'SC', name: 'Seychelles' },
		{ code: 'SL', name: 'Sierra Leone' },
		{ code: 'SG', name: 'Singapore' },
		{ code: 'SK', name: 'Slovakia' },
		{ code: 'SI', name: 'Slovenia' },
		{ code: 'SB', name: 'Solomon Islands' },
		{ code: 'SO', name: 'Somalia' },
		{ code: 'ZA', name: 'South Africa' },
		{ code: 'SS', name: 'South Sudan' },
		{ code: 'ES', name: 'Spain' },
		{ code: 'LK', name: 'Sri Lanka' },
		{ code: 'SD', name: 'Sudan' },
		{ code: 'SR', name: 'Suriname' },
		{ code: 'SE', name: 'Sweden' },
		{ code: 'CH', name: 'Switzerland' },
		{ code: 'SY', name: 'Syria' },
		{ code: 'TW', name: 'Taiwan' },
		{ code: 'TJ', name: 'Tajikistan' },
		{ code: 'TZ', name: 'Tanzania' },
		{ code: 'TH', name: 'Thailand' },
		{ code: 'TL', name: 'Timor-Leste' },
		{ code: 'TG', name: 'Togo' },
		{ code: 'TO', name: 'Tonga' },
		{ code: 'TT', name: 'Trinidad and Tobago' },
		{ code: 'TN', name: 'Tunisia' },
		{ code: 'TR', name: 'Turkey' },
		{ code: 'TM', name: 'Turkmenistan' },
		{ code: 'TV', name: 'Tuvalu' },
		{ code: 'UG', name: 'Uganda' },
		{ code: 'UA', name: 'Ukraine' },
		{ code: 'AE', name: 'United Arab Emirates' },
		{ code: 'GB', name: 'United Kingdom' },
		{ code: 'US', name: 'United States' },
		{ code: 'UY', name: 'Uruguay' },
		{ code: 'UZ', name: 'Uzbekistan' },
		{ code: 'VU', name: 'Vanuatu' },
		{ code: 'VA', name: 'Vatican City' },
		{ code: 'VE', name: 'Venezuela' },
		{ code: 'VN', name: 'Vietnam' },
		{ code: 'YE', name: 'Yemen' },
		{ code: 'ZM', name: 'Zambia' },
		{ code: 'ZW', name: 'Zimbabwe' }
	];

function validate() {
    const newErrors = {};
    
    // First Name - required
    if (!formData.firstName.trim()) {
      newErrors.firstName = 'First name is required';
    }
    
    // Last Name - required
    if (!formData.lastName.trim()) {
      newErrors.lastName = 'Last name is required';
    }
    
    // Company - required
    if (!formData.company.trim()) {
      newErrors.company = 'Company name is required';
    }
    
    // Email - required + format validation
    if (!formData.email.trim()) {
      newErrors.email = 'Email is required';
    } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.email)) {
      newErrors.email = 'Please enter a valid email address';
    }
    
    // Phone - required + basic format
    if (!formData.phone.trim()) {
      newErrors.phone = 'Business phone is required';
    } else if (!/^[\d\s\-\+\(\)]{7,20}$/.test(formData.phone)) {
      newErrors.phone = 'Please enter a valid phone number';
    }
    
    // Country - required
    if (!formData.country) {
      newErrors.country = 'Please select your country';
    }
    
    errors = newErrors;
    return Object.keys(newErrors).length === 0;
  }
  
  // Clear error when user starts typing
  function clearError(field) {
    if (errors[field]) {
      errors = { ...errors, [field]: undefined };
    }
  }

   async function handleSubmit(e) {
    e.preventDefault();
    
    if (!validate()) {
      // Scroll to first error
      const firstError = document.querySelector('.error-message');
      firstError?.scrollIntoView({ behavior: 'smooth', block: 'center' });
      return;
    }
    
    isSubmitting = true;
    
    try {
      // Replace with your actual API endpoint
      const response = await fetch('/api/contact', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(formData)
      });
      
      if (response.ok) {
        submitSuccess = true;
        // Reset form
        formData = {
          firstName: '',
          lastName: '',
          company: '',
          email: '',
          phone: '',
          country: '',
          message: ''
        };
      } else {
        throw new Error('Submission failed');
      }
    } catch (error) {
      console.error('Form submission error:', error);
      errors = { ...errors, submit: 'Something went wrong. Please try again.' };
    } finally {
      isSubmitting = false;
    }
  }
    
</script>

<Section bgClass="bg-[#f0f1f7]">
	<Container class="pt-20">
		<div class="flex">
			<div class="flex-col items-start justify-center pt-4 pr-2">
				<div class=" text-[#0e329b] font-semibold text-[1.7rem] w-full flex mb-6">
					<h2>Start Your Thuraya-4 Deployment</h2>
				</div>
				<div class="font-antartica font-light text-[1rem] text-[#666666] mb-12 pr-12">
					<p>Speak with a specialist on products, services, and timelines</p>
				</div>
				<div class="font-antartica font-light text-[0.7rem] text-[#666666]">
					<p>* Mandatory Field</p>
				</div>
			</div>

			<form class="flex flex-col gap-4 w-[50rem] mx-auto py-4 text-[0.9rem] mb-25">
				<div class="flex gap-4">
					<input class="flex-1 form-input" type="text" placeholder="First Name *" />
					<input class="flex-1 form-input" type="text" placeholder="Last Name *" />
				</div>
				<input class="flex-1 form-input" type="text" placeholder="Company Name *" />
				<input class="flex-1 form-input" type="email" placeholder="E-Mail *" />
				<input class="flex-1 form-input" type="tel" placeholder="Business Phone *" />

				<select
					class="w-full px-4 py-4 bg-white rounded-lg border border-transparent
         focus:border-blue-500 focus:outline-none focus:ring-2 focus:ring-blue-500/20
         text-gray-400 appearance-block cursor-pointer
         bg-[url('data:image/svg+xml,...')] bg-no-repeat bg-[right_1rem_center]"
				>
					<option>Select your Country *</option>
				</select>
				<div class="flex h-50">
					<textarea
						class="w-full px-4 py-4 bg-white rounded-lg border border-transparent
         focus:border-blue-500 focus:outline-none focus:ring-2 focus:ring-blue-500/20
         placeholder:text-gray-400 transition-colors resize-none min-h-32"
						placeholder="Message"
					></textarea>
				</div>

				<div class="flex items-center justify-end mt-3">
					<button
						class="bg-[#0e329b] rounded-sm w-[45%] text-white p-3 font-antarctica font-semibold flex items-center justify-center text-[0.8rem]"
						type="submit">SUBMIT</button
					>
				</div>
			</form>
		</div>
	</Container>
</Section> -->

<script>
	// ============================================
	// STATE MANAGEMENT (Svelte 5 Runes)
	// ============================================

	import Container from './Container.svelte';
	import Section from './Section.svelte';

	let formData = $state({
		firstName: '',
		lastName: '',
		company: '',
		email: '',
		phone: '',
		country: '',
		message: ''
	});

	let errors = $state({});
	let isSubmitting = $state(false);
	let submitSuccess = $state(false);

	// ============================================
	// COUNTRIES LIST (ISO 3166-1)
	// ============================================

	const countries = [
		{ code: 'AF', name: 'Afghanistan' },
		{ code: 'AL', name: 'Albania' },
		{ code: 'DZ', name: 'Algeria' },
		{ code: 'AD', name: 'Andorra' },
		{ code: 'AO', name: 'Angola' },
		{ code: 'AG', name: 'Antigua and Barbuda' },
		{ code: 'AR', name: 'Argentina' },
		{ code: 'AM', name: 'Armenia' },
		{ code: 'AU', name: 'Australia' },
		{ code: 'AT', name: 'Austria' },
		{ code: 'AZ', name: 'Azerbaijan' },
		{ code: 'BS', name: 'Bahamas' },
		{ code: 'BH', name: 'Bahrain' },
		{ code: 'BD', name: 'Bangladesh' },
		{ code: 'BB', name: 'Barbados' },
		{ code: 'BY', name: 'Belarus' },
		{ code: 'BE', name: 'Belgium' },
		{ code: 'BZ', name: 'Belize' },
		{ code: 'BJ', name: 'Benin' },
		{ code: 'BT', name: 'Bhutan' },
		{ code: 'BO', name: 'Bolivia' },
		{ code: 'BA', name: 'Bosnia and Herzegovina' },
		{ code: 'BW', name: 'Botswana' },
		{ code: 'BR', name: 'Brazil' },
		{ code: 'BN', name: 'Brunei' },
		{ code: 'BG', name: 'Bulgaria' },
		{ code: 'BF', name: 'Burkina Faso' },
		{ code: 'BI', name: 'Burundi' },
		{ code: 'CV', name: 'Cabo Verde' },
		{ code: 'KH', name: 'Cambodia' },
		{ code: 'CM', name: 'Cameroon' },
		{ code: 'CA', name: 'Canada' },
		{ code: 'CF', name: 'Central African Republic' },
		{ code: 'TD', name: 'Chad' },
		{ code: 'CL', name: 'Chile' },
		{ code: 'CN', name: 'China' },
		{ code: 'CO', name: 'Colombia' },
		{ code: 'KM', name: 'Comoros' },
		{ code: 'CG', name: 'Congo' },
		{ code: 'CD', name: 'Congo (Democratic Republic)' },
		{ code: 'CR', name: 'Costa Rica' },
		{ code: 'CI', name: "Côte d'Ivoire" },
		{ code: 'HR', name: 'Croatia' },
		{ code: 'CU', name: 'Cuba' },
		{ code: 'CY', name: 'Cyprus' },
		{ code: 'CZ', name: 'Czech Republic' },
		{ code: 'DK', name: 'Denmark' },
		{ code: 'DJ', name: 'Djibouti' },
		{ code: 'DM', name: 'Dominica' },
		{ code: 'DO', name: 'Dominican Republic' },
		{ code: 'EC', name: 'Ecuador' },
		{ code: 'EG', name: 'Egypt' },
		{ code: 'SV', name: 'El Salvador' },
		{ code: 'GQ', name: 'Equatorial Guinea' },
		{ code: 'ER', name: 'Eritrea' },
		{ code: 'EE', name: 'Estonia' },
		{ code: 'SZ', name: 'Eswatini' },
		{ code: 'ET', name: 'Ethiopia' },
		{ code: 'FJ', name: 'Fiji' },
		{ code: 'FI', name: 'Finland' },
		{ code: 'FR', name: 'France' },
		{ code: 'GA', name: 'Gabon' },
		{ code: 'GM', name: 'Gambia' },
		{ code: 'GE', name: 'Georgia' },
		{ code: 'DE', name: 'Germany' },
		{ code: 'GH', name: 'Ghana' },
		{ code: 'GR', name: 'Greece' },
		{ code: 'GD', name: 'Grenada' },
		{ code: 'GT', name: 'Guatemala' },
		{ code: 'GN', name: 'Guinea' },
		{ code: 'GW', name: 'Guinea-Bissau' },
		{ code: 'GY', name: 'Guyana' },
		{ code: 'HT', name: 'Haiti' },
		{ code: 'HN', name: 'Honduras' },
		{ code: 'HU', name: 'Hungary' },
		{ code: 'IS', name: 'Iceland' },
		{ code: 'IN', name: 'India' },
		{ code: 'ID', name: 'Indonesia' },
		{ code: 'IR', name: 'Iran' },
		{ code: 'IQ', name: 'Iraq' },
		{ code: 'IE', name: 'Ireland' },
		{ code: 'IL', name: 'Israel' },
		{ code: 'IT', name: 'Italy' },
		{ code: 'JM', name: 'Jamaica' },
		{ code: 'JP', name: 'Japan' },
		{ code: 'JO', name: 'Jordan' },
		{ code: 'KZ', name: 'Kazakhstan' },
		{ code: 'KE', name: 'Kenya' },
		{ code: 'KI', name: 'Kiribati' },
		{ code: 'KP', name: 'Korea (North)' },
		{ code: 'KR', name: 'Korea (South)' },
		{ code: 'KW', name: 'Kuwait' },
		{ code: 'KG', name: 'Kyrgyzstan' },
		{ code: 'LA', name: 'Laos' },
		{ code: 'LV', name: 'Latvia' },
		{ code: 'LB', name: 'Lebanon' },
		{ code: 'LS', name: 'Lesotho' },
		{ code: 'LR', name: 'Liberia' },
		{ code: 'LY', name: 'Libya' },
		{ code: 'LI', name: 'Liechtenstein' },
		{ code: 'LT', name: 'Lithuania' },
		{ code: 'LU', name: 'Luxembourg' },
		{ code: 'MG', name: 'Madagascar' },
		{ code: 'MW', name: 'Malawi' },
		{ code: 'MY', name: 'Malaysia' },
		{ code: 'MV', name: 'Maldives' },
		{ code: 'ML', name: 'Mali' },
		{ code: 'MT', name: 'Malta' },
		{ code: 'MH', name: 'Marshall Islands' },
		{ code: 'MR', name: 'Mauritania' },
		{ code: 'MU', name: 'Mauritius' },
		{ code: 'MX', name: 'Mexico' },
		{ code: 'FM', name: 'Micronesia' },
		{ code: 'MD', name: 'Moldova' },
		{ code: 'MC', name: 'Monaco' },
		{ code: 'MN', name: 'Mongolia' },
		{ code: 'ME', name: 'Montenegro' },
		{ code: 'MA', name: 'Morocco' },
		{ code: 'MZ', name: 'Mozambique' },
		{ code: 'MM', name: 'Myanmar' },
		{ code: 'NA', name: 'Namibia' },
		{ code: 'NR', name: 'Nauru' },
		{ code: 'NP', name: 'Nepal' },
		{ code: 'NL', name: 'Netherlands' },
		{ code: 'NZ', name: 'New Zealand' },
		{ code: 'NI', name: 'Nicaragua' },
		{ code: 'NE', name: 'Niger' },
		{ code: 'NG', name: 'Nigeria' },
		{ code: 'MK', name: 'North Macedonia' },
		{ code: 'NO', name: 'Norway' },
		{ code: 'OM', name: 'Oman' },
		{ code: 'PK', name: 'Pakistan' },
		{ code: 'PW', name: 'Palau' },
		{ code: 'PS', name: 'Palestine' },
		{ code: 'PA', name: 'Panama' },
		{ code: 'PG', name: 'Papua New Guinea' },
		{ code: 'PY', name: 'Paraguay' },
		{ code: 'PE', name: 'Peru' },
		{ code: 'PH', name: 'Philippines' },
		{ code: 'PL', name: 'Poland' },
		{ code: 'PT', name: 'Portugal' },
		{ code: 'QA', name: 'Qatar' },
		{ code: 'RO', name: 'Romania' },
		{ code: 'RU', name: 'Russia' },
		{ code: 'RW', name: 'Rwanda' },
		{ code: 'KN', name: 'Saint Kitts and Nevis' },
		{ code: 'LC', name: 'Saint Lucia' },
		{ code: 'VC', name: 'Saint Vincent and the Grenadines' },
		{ code: 'WS', name: 'Samoa' },
		{ code: 'SM', name: 'San Marino' },
		{ code: 'ST', name: 'Sao Tome and Principe' },
		{ code: 'SA', name: 'Saudi Arabia' },
		{ code: 'SN', name: 'Senegal' },
		{ code: 'RS', name: 'Serbia' },
		{ code: 'SC', name: 'Seychelles' },
		{ code: 'SL', name: 'Sierra Leone' },
		{ code: 'SG', name: 'Singapore' },
		{ code: 'SK', name: 'Slovakia' },
		{ code: 'SI', name: 'Slovenia' },
		{ code: 'SB', name: 'Solomon Islands' },
		{ code: 'SO', name: 'Somalia' },
		{ code: 'ZA', name: 'South Africa' },
		{ code: 'SS', name: 'South Sudan' },
		{ code: 'ES', name: 'Spain' },
		{ code: 'LK', name: 'Sri Lanka' },
		{ code: 'SD', name: 'Sudan' },
		{ code: 'SR', name: 'Suriname' },
		{ code: 'SE', name: 'Sweden' },
		{ code: 'CH', name: 'Switzerland' },
		{ code: 'SY', name: 'Syria' },
		{ code: 'TW', name: 'Taiwan' },
		{ code: 'TJ', name: 'Tajikistan' },
		{ code: 'TZ', name: 'Tanzania' },
		{ code: 'TH', name: 'Thailand' },
		{ code: 'TL', name: 'Timor-Leste' },
		{ code: 'TG', name: 'Togo' },
		{ code: 'TO', name: 'Tonga' },
		{ code: 'TT', name: 'Trinidad and Tobago' },
		{ code: 'TN', name: 'Tunisia' },
		{ code: 'TR', name: 'Turkey' },
		{ code: 'TM', name: 'Turkmenistan' },
		{ code: 'TV', name: 'Tuvalu' },
		{ code: 'UG', name: 'Uganda' },
		{ code: 'UA', name: 'Ukraine' },
		{ code: 'AE', name: 'United Arab Emirates' },
		{ code: 'GB', name: 'United Kingdom' },
		{ code: 'US', name: 'United States' },
		{ code: 'UY', name: 'Uruguay' },
		{ code: 'UZ', name: 'Uzbekistan' },
		{ code: 'VU', name: 'Vanuatu' },
		{ code: 'VA', name: 'Vatican City' },
		{ code: 'VE', name: 'Venezuela' },
		{ code: 'VN', name: 'Vietnam' },
		{ code: 'YE', name: 'Yemen' },
		{ code: 'ZM', name: 'Zambia' },
		{ code: 'ZW', name: 'Zimbabwe' }
	];

	// ============================================
	// VALIDATION
	// ============================================

	function validate() {
		const newErrors = {};

		// First Name - required
		if (!formData.firstName.trim()) {
			newErrors.firstName = 'First name is required';
		}

		// Last Name - required
		if (!formData.lastName.trim()) {
			newErrors.lastName = 'Last name is required';
		}

		// Company - required
		if (!formData.company.trim()) {
			newErrors.company = 'Company name is required';
		}

		// Email - required + format validation
		if (!formData.email.trim()) {
			newErrors.email = 'Email is required';
		} else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.email)) {
			newErrors.email = 'Please enter a valid email address';
		}

		// Phone - required + basic format
		if (!formData.phone.trim()) {
			newErrors.phone = 'Business phone is required';
		} else if (!/^[\d\s\-\+\(\)]{7,20}$/.test(formData.phone)) {
			newErrors.phone = 'Please enter a valid phone number';
		}

		// Country - required
		if (!formData.country) {
			newErrors.country = 'Please select your country';
		}

		errors = newErrors;
		return Object.keys(newErrors).length === 0;
	}

	// Clear error when user starts typing
	function clearError(field) {
		if (errors[field]) {
			errors = { ...errors, [field]: undefined };
		}
	}

	// ============================================
	// FORM SUBMISSION
	// ============================================

	async function handleSubmit(e) {
		e.preventDefault();

		if (!validate()) {
			// Scroll to first error
			const firstError = document.querySelector('.error-message');
			firstError?.scrollIntoView({ behavior: 'smooth', block: 'center' });
			return;
		}

		isSubmitting = true;

		try {
			// Replace with your actual API endpoint
			const response = await fetch('/api/contact', {
				method: 'POST',
				headers: { 'Content-Type': 'application/json' },
				body: JSON.stringify(formData)
			});

			if (response.ok) {
				submitSuccess = true;
				// Reset form
				formData = {
					firstName: '',
					lastName: '',
					company: '',
					email: '',
					phone: '',
					country: '',
					message: ''
				};
			} else {
				throw new Error('Submission failed');
			}
		} catch (error) {
			console.error('Form submission error:', error);
			errors = { ...errors, submit: 'Something went wrong. Please try again.' };
		} finally {
			isSubmitting = false;
		}
	}
</script>

<!-- ============================================
     FORM TEMPLATE
     ============================================ -->

<Section bgClass="bg-[#f0f1f7]">
	<Container class="md:flex md:flex-row items-start justify-center py-25 w-full flex-col">
		<div class="flex-col items-start justify-center w-full">
			<div
				class=" text-[#0e329b] font-semibold sm:text-[1.7rem] text-[1.3rem] w-full flex mb-6 sm:pr-0 sm:pr-10 text-center sm:text-left"
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
		<div class="w-full flex sm:text-[1rem] text-[0.8rem]">
			<form onsubmit={handleSubmit} class=" mx-auto flex flex-col gap-4" novalidate>
				<!-- Success Message -->
				{#if submitSuccess}
					<div class="bg-green-50 border border-green-200 text-green-800 px-6 py-4 rounded-lg mb-4">
						<p class="font-medium">Thank you for your message!</p>
						<p class="text-sm mt-1">We'll get back to you shortly.</p>
					</div>
				{/if}

				<!-- Row 1: First Name + Last Name -->
				<div class="flex flex-col sm:flex-row gap-4">
					<!-- First Name -->
					<div class="flex-1">
						<label for="firstName" class="sr-only">First Name</label>
						<input
							id="firstName"
							type="text"
							placeholder="First Name *"
							bind:value={formData.firstName}
							oninput={() => clearError('firstName')}
							class="w-full px-5 py-4 bg-white rounded-lg border transition-all duration-200
                 placeholder:text-gray-400 text-gray-700
                 {errors.firstName
								? 'border-red-400 focus:border-red-500 focus:ring-red-500/20'
								: 'border-gray-200 focus:border-blue-500 focus:ring-blue-500/20'}
                 focus:outline-none focus:ring-4"
							aria-invalid={errors.firstName ? 'true' : 'false'}
							aria-describedby={errors.firstName ? 'firstName-error' : undefined}
						/>
						{#if errors.firstName}
							<p id="firstName-error" class="error-message text-red-500 text-sm mt-1.5 ml-1">
								{errors.firstName}
							</p>
						{/if}
					</div>

					<!-- Last Name -->
					<div class="flex-1">
						<label for="lastName" class="sr-only">Last Name</label>
						<input
							id="lastName"
							type="text"
							placeholder="Last Name *"
							bind:value={formData.lastName}
							oninput={() => clearError('lastName')}
							class="w-full px-5 py-4 bg-white rounded-lg border transition-all duration-200
                 placeholder:text-gray-400 text-gray-700
                 {errors.lastName
								? 'border-red-400 focus:border-red-500 focus:ring-red-500/20'
								: 'border-gray-200 focus:border-blue-500 focus:ring-blue-500/20'}
                 focus:outline-none focus:ring-4"
							aria-invalid={errors.lastName ? 'true' : 'false'}
							aria-describedby={errors.lastName ? 'lastName-error' : undefined}
						/>
						{#if errors.lastName}
							<p id="lastName-error" class="error-message text-red-500 text-sm mt-1.5 ml-1">
								{errors.lastName}
							</p>
						{/if}
					</div>
				</div>

				<!-- Company Name -->
				<div>
					<label for="company" class="sr-only">Company Name</label>
					<input
						id="company"
						type="text"
						placeholder="Company Name *"
						bind:value={formData.company}
						oninput={() => clearError('company')}
						class="w-full px-5 py-4 bg-white rounded-lg border transition-all duration-200
               placeholder:text-gray-400 text-gray-700
               {errors.company
							? 'border-red-400 focus:border-red-500 focus:ring-red-500/20'
							: 'border-gray-200 focus:border-blue-500 focus:ring-blue-500/20'}
               focus:outline-none focus:ring-4"
						aria-invalid={errors.company ? 'true' : 'false'}
						aria-describedby={errors.company ? 'company-error' : undefined}
					/>
					{#if errors.company}
						<p id="company-error" class="error-message text-red-500 text-sm mt-1.5 ml-1">
							{errors.company}
						</p>
					{/if}
				</div>

				<!-- Email -->
				<div>
					<label for="email" class="sr-only">Email</label>
					<input
						id="email"
						type="email"
						placeholder="E-Mail *"
						bind:value={formData.email}
						oninput={() => clearError('email')}
						class="w-full px-5 py-4 bg-white rounded-lg border transition-all duration-200
               placeholder:text-gray-400 text-gray-700
               {errors.email
							? 'border-red-400 focus:border-red-500 focus:ring-red-500/20'
							: 'border-gray-200 focus:border-blue-500 focus:ring-blue-500/20'}
               focus:outline-none focus:ring-4"
						aria-invalid={errors.email ? 'true' : 'false'}
						aria-describedby={errors.email ? 'email-error' : undefined}
					/>
					{#if errors.email}
						<p id="email-error" class="error-message text-red-500 text-sm mt-1.5 ml-1">
							{errors.email}
						</p>
					{/if}
				</div>

				<!-- Business Phone -->
				<div>
					<label for="phone" class="sr-only">Business Phone</label>
					<input
						id="phone"
						type="tel"
						placeholder="Business Phone *"
						bind:value={formData.phone}
						oninput={() => clearError('phone')}
						class="w-full px-5 py-4 bg-white rounded-lg border transition-all duration-200
               placeholder:text-gray-400 text-gray-700
               {errors.phone
							? 'border-red-400 focus:border-red-500 focus:ring-red-500/20'
							: 'border-gray-200 focus:border-blue-500 focus:ring-blue-500/20'}
               focus:outline-none focus:ring-4"
						aria-invalid={errors.phone ? 'true' : 'false'}
						aria-describedby={errors.phone ? 'phone-error' : undefined}
					/>
					{#if errors.phone}
						<p id="phone-error" class="error-message text-red-500 text-sm mt-1.5 ml-1">
							{errors.phone}
						</p>
					{/if}
				</div>

				<!-- Country Select -->
				<div class="relative">
					<label for="country" class="sr-only">Country</label>
					<select
						id="country"
						bind:value={formData.country}
						onchange={() => clearError('country')}
						class="w-full px-5 py-4 bg-white rounded-lg border transition-all duration-200
               appearance-none cursor-pointer
               {!formData.country ? 'text-gray-400' : 'text-gray-700'}
               {errors.country
							? 'border-red-400 focus:border-red-500 focus:ring-red-500/20'
							: 'border-gray-200 focus:border-blue-500 focus:ring-blue-500/20'}
               focus:outline-none focus:ring-4"
						aria-invalid={errors.country ? 'true' : 'false'}
						aria-describedby={errors.country ? 'country-error' : undefined}
					>
						<option value="" disabled>Select your Country *</option>
						{#each countries as country}
							<option value={country.code}>{country.name}</option>
						{/each}
					</select>

					<!-- Custom dropdown arrow -->
					<div class="absolute right-4 top-1/2 -translate-y-1/2 pointer-events-none">
						<svg
							class="w-5 h-5 text-gray-400"
							fill="none"
							stroke="currentColor"
							viewBox="0 0 24 24"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								stroke-width="2"
								d="M19 9l-7 7-7-7"
							/>
						</svg>
					</div>

					{#if errors.country}
						<p id="country-error" class="error-message text-red-500 text-sm mt-1.5 ml-1">
							{errors.country}
						</p>
					{/if}
				</div>

				<!-- Message -->
				<div>
					<label for="message" class="sr-only">Message</label>
					<textarea
						id="message"
						placeholder="Message"
						bind:value={formData.message}
						rows="5"
						class="w-full px-5 py-4 bg-white rounded-lg border border-gray-200 transition-all duration-200
               placeholder:text-gray-400 text-gray-700 resize-none
               focus:border-blue-500 focus:outline-none focus:ring-4 focus:ring-blue-500/20"
					></textarea>
				</div>

				<!-- Submit Error -->
				{#if errors.submit}
					<p class="text-red-500 text-sm text-center">{errors.submit}</p>
				{/if}

				<!-- Submit Button -->
				<div class="flex sm:justify-end justify-center sm:text-[1rem] text-[0.8rem] mt-2">
					<button
						type="submit"
						disabled={isSubmitting}
						class="px-14 py-4 bg-blue-800 text-white font-semibold tracking-wider rounded-lg
               hover:bg-blue-900 active:scale-[0.98] transition-all duration-200
               disabled:opacity-60 disabled:cursor-not-allowed disabled:active:scale-100
               focus:outline-none focus:ring-4 focus:ring-blue-500/30"
					>
						{#if isSubmitting}
							<span class="flex items-center gap-2">
								<svg class="animate-spin h-5 w-5" viewBox="0 0 24 24">
									<circle
										class="opacity-25"
										cx="12"
										cy="12"
										r="10"
										stroke="currentColor"
										stroke-width="4"
										fill="none"
									/>
									<path
										class="opacity-75"
										fill="currentColor"
										d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"
									/>
								</svg>
								SUBMITTING...
							</span>
						{:else}
							SUBMIT
						{/if}
					</button>
				</div>
			</form>
		</div>
	</Container>
</Section>
