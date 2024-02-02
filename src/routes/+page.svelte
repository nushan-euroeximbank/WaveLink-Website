<script>
	import {
		Section,
		News,
		HeroHeader,
		FeatureDefault,
		FeatureItem,
		Cta
	} from 'flowbite-svelte-blocks';
	import {
		Button,
		Card,
		Label,
		Input,
		Modal,
		Textarea,
		Select,
		Radio,
		Alert
	} from 'flowbite-svelte';

	import {
		ArrowRightSolid,
		ArrowRightOutline,
		InfoCircleSolid,
		ChartSolid,
		DollarSolid,
		CashSolid,
		SalePercentSolid,
		EnvelopeSolid
	} from 'flowbite-svelte-icons';

	import { signUpModal } from '$lib/stores';

	let defaultModal = false;

	let dismissable = false;

	signUpModal.subscribe((value) => {
		defaultModal = value;
	});

	const toggleModal = () => {
		signUpModal.update((value) => !value);
	};

	$: $signUpModal = defaultModal;

	let countries = [
		{ value: 'United States', name: 'United States' },
		{ value: 'Europe', name: 'Europe' },
		{ value: 'Africa', name: 'Africa' },
		{ value: 'India', name: 'India' }
	];

	// Company Administrator, Senior Manager, Employee, Contractor, Director, Owner, Other
	let roles = [
		{ value: 'Company Administrator', name: 'Company Administrator' },
		{ value: 'Senior Manager', name: 'Senior Manager' },
		{ value: 'Employee', name: 'Employee' },
		{ value: 'Contractor', name: 'Contractor' },
		{ value: 'Director', name: 'Director' },
		{ value: 'Owner', name: 'Owner' },
		{ value: 'Other', name: 'Other' }
	];

	let data = {
		// S1
		geoArea: '',
		paymentType: '',
		// S2
		fullName: '',
		email: '',
		country: '',
		state: '',
		city: '',
		zip: '',
		phone: '',
		// S3
		businessName: '',
		registeredAddress: '',
		businessAddress: '',
		websiteURL: '',
		// S4
		businessDescription: '',
		yourRole: '',
		otherRole: ''
	};

	let errorMessage = '';

	let slide = 1;
	let showAll = false;

	const nextSlide = () => {
		if (slide === 1 && data.geoArea === '') {
			errorMessage = 'Please select the area of operations';
			return;
		}
		if (slide === 1 && data.paymentType === '') {
			errorMessage = 'Please select the payment type';
			return;
		}
		if (slide === 2 && data.fullName === '') {
			errorMessage = 'Please enter your full name';
			return;
		}
		if (slide === 2 && data.email === '') {
			errorMessage = 'Please enter your email address';
			return;
		}
		if (slide === 2 && data.country === '') {
			errorMessage = 'Please enter your country';
			return;
		}
		if (slide === 2 && data.state === '') {
			errorMessage = 'Please enter your state';
			return;
		}
		if (slide === 2 && data.city === '') {
			errorMessage = 'Please enter your city';
			return;
		}
		if (slide === 2 && data.zip === '') {
			errorMessage = 'Please enter your zip code';
			return;
		}
		if (slide === 2 && data.phone === '') {
			errorMessage = 'Please enter your phone number';
			return;
		}
		if (slide === 3 && data.businessName === '') {
			errorMessage = 'Please enter your business name';
			return;
		}
		if (slide === 3 && data.registeredAddress === '') {
			errorMessage = 'Please enter your registered address';
			return;
		}
		if (slide === 3 && data.businessAddress === '') {
			errorMessage = 'Please enter your business address';
			return;
		}
		if (slide === 3 && data.websiteURL === '') {
			errorMessage = 'Please enter your website URL';
			return;
		}
		if (slide === 4 && data.businessDescription === '') {
			errorMessage = 'Please enter your business description';
			return;
		}
		if (slide === 4 && data.yourRole === '') {
			errorMessage = 'Please enter your role';
			return;
		}
		if (slide === 4 && data.yourRole === 'Other' && data.otherRole === '') {
			errorMessage = 'Please enter your role';
			return;
		}

		if (slide === 4) {
			showAll = true;
		}
		errorMessage = '';
		slide += 1;
	};

	const prevSlide = () => {
		if (slide === 1) return;
		if (slide === 5) {
			showAll = false;
		}
		slide -= 1;
	};

	let FORMSPARK_ACTION_URL = 'https://submit-form.com/gqyflXzr';

	const onSubmit = async () => {
		try {
			await fetch(FORMSPARK_ACTION_URL, {
				method: 'POST',
				headers: {
					'Content-Type': 'application/json',
					Accept: 'application/json'
				},
				body: JSON.stringify(data)
			});
		} catch (error) {
			slide = 104;
			showAll = true;
			errorMessage = 'Something went wrong while submitting the form. Please try again later.';
			dismissable = true;
		} finally {
			slide = 200;
			showAll = false;
			dismissable = true;
		}
	};
</script>

<svelte:head>
	<title>Wave-Link | Home</title>
</svelte:head>

<!-- Hero Section -->

<div
	class="flex h-screen flex-row items-center justify-center bg-[url('https://unsplash.com/photos/axAbxUA32hE/download?ixid=M3wxMjA3fDF8MXxhbGx8MXx8fHx8fDJ8fDE3MDY3OTc4MTh8&force=true&w=1920')] bg-cover"
>
	<Section name="heroDefault">
		<div class="mb-4">
			<News href="/signup">
				<span class="mr-3 rounded-full bg-primary-600 px-4 py-1.5 text-xs text-white">New</span>
				<span class="text-sm font-medium">Support in New Geographical Areas</span>
			</News>
		</div>
		<HeroHeader pClass="text-white mix-blend-exclusion">
			<svelte:fragment slot="h1">The Key To A Universe Of Possibilities</svelte:fragment>
			<svelte:fragment slot="paragraph"
				>Your Wavelink account is the key that opens a world of possibilities. Wavelink connects
				your business to the world, whether it’s making international payments, receiving funds,
				managing your digital business, or accessing capital.</svelte:fragment
			>
		</HeroHeader>

		<div
			class="mb-8 mt-4 flex flex-col space-y-4 sm:flex-row sm:justify-center sm:space-x-4 sm:space-y-0 lg:mb-16"
		>
			<Button size="lg" on:click={toggleModal}>
				Join Today <ArrowRightSolid size="md" class="-mr-1 ml-2" />
			</Button>
		</div>
	</Section>
</div>

<!-- Services Section -->

<div class="flex min-h-screen flex-col items-center justify-center p-8">
	<HeroHeader
		class="mx-auto mb-8 max-w-screen-md text-center lg:mb-16"
		h2Class="mb-4 text-4xl tracking-tight font-extrabold text-gray-900 dark:text-white"
		pClass="text-gray-500 sm:text-xl dark:text-gray-400"
	>
		<svelte:fragment slot="h2">Designed for business teams like yours</svelte:fragment>
		<svelte:fragment slot="paragraph"
			>Here at Flowbite we focus on markets where technology, innovation, and capital can unlock
			long-term value and drive economic growth.</svelte:fragment
		>
	</HeroHeader>
	<Section name="feature">
		<FeatureDefault
			divClass="space-y-8 md:grid md:grid-cols-2 lg:grid-cols-3 md:gap-12 md:space-y-0"
		>
			<FeatureItem>
				<svelte:fragment slot="icon"
					><ChartSolid class="text-primary-600 dark:text-primary-300" /></svelte:fragment
				>
				<svelte:fragment slot="h3">Much Affordable</svelte:fragment>
				<svelte:fragment slot="paragraph"
					>Avoid high currency exchange conversion rates with Wavelink. No exchange fee during
					processing</svelte:fragment
				>
			</FeatureItem>
			<FeatureItem>
				<svelte:fragment slot="icon"
					><CashSolid class="text-primary-600 dark:text-primary-300" /></svelte:fragment
				>
				<svelte:fragment slot="h3">No Currency Fee</svelte:fragment>
				<svelte:fragment slot="paragraph"
					>Receive money from all over the world without currency fees</svelte:fragment
				>
			</FeatureItem>
			<FeatureItem>
				<svelte:fragment slot="icon"
					><SalePercentSolid class="text-primary-600 dark:text-primary-300" /></svelte:fragment
				>
				<svelte:fragment slot="h3">Versatile</svelte:fragment>
				<svelte:fragment slot="paragraph"
					>Receive payments from your customers in any currency</svelte:fragment
				>
			</FeatureItem>
			<FeatureItem>
				<svelte:fragment slot="icon"
					><DollarSolid class="text-primary-600 dark:text-primary-300" /></svelte:fragment
				>
				<svelte:fragment slot="h3">Local Support</svelte:fragment>
				<svelte:fragment slot="paragraph"
					>Transfer your money to your local bank accounts</svelte:fragment
				>
			</FeatureItem>
			<FeatureItem>
				<svelte:fragment slot="icon"
					><EnvelopeSolid class="text-primary-600 dark:text-primary-300" /></svelte:fragment
				>
				<svelte:fragment slot="h3">No hidden fees</svelte:fragment>
				<svelte:fragment slot="paragraph"
					>You will not receive any hidden fee by using any of our services</svelte:fragment
				>
			</FeatureItem>
		</FeatureDefault>
	</Section>
</div>

<!-- CTA -->

<div
	class="flex min-h-screen flex-row items-center justify-center bg-[url('https://unsplash.com/photos/HocQ5RQ4Qpo/download?ixid=M3wxMjA3fDB8MXxhbGx8NHx8fHx8fDJ8fDE3MDY3OTk2MjJ8&force=true&w=1920')] bg-cover"
>
	<Section name="ctawithimg">
		<Cta ctatype="image">
			<svelte:fragment slot="img">
				<img
					class="w-full dark:hidden"
					src="https://flowbite.s3.amazonaws.com/blocks/marketing-ui/cta/cta-dashboard-mockup.svg"
					alt="dashboard"
				/>
				<img
					class="hidden w-full dark:block"
					src="https://flowbite.s3.amazonaws.com/blocks/marketing-ui/cta/cta-dashboard-mockup-dark.svg"
					alt="dashboard"
				/>
			</svelte:fragment>
			<h2 class="text-3xl font-bold text-white">Avoid Extra Fees for Currency Exchange</h2>
			<p class="mb-6 font-light text-white md:text-lg">
				Avoid high currency exchange conversion rates with Wavelink. No exchange fee during
				processing
			</p>
			<button
				on:click={toggleModal}
				class="inline-flex items-center rounded-lg bg-primary-700 px-5 py-2.5 text-center text-sm font-medium text-white hover:bg-primary-800 focus:ring-4 focus:ring-primary-300 dark:focus:ring-primary-900"
			>
				Get started
				<ArrowRightSolid size="md" class="-mr-1 ml-2" />
			</button>
		</Cta>
	</Section>
</div>

<!-- Onboarding Process -->
<div class="flex min-h-screen flex-col items-center justify-center p-4">
	<h2 class="text-3xl font-bold">Easy functionality</h2>
	<p class="mb-6 max-w-4xl text-center font-light text-gray-500 dark:text-gray-400 md:text-lg">
		Create an account from us or use your own bank account Run your business in any part of the
		world in few simple clicks Operate easily for any industry
	</p>

	<ol class="mt-8 flex flex-col items-start md:max-w-6xl md:flex-row">
		<li class="relative mb-6 sm:mb-0 md:w-1/3">
			<div class="flex items-center">
				<div
					class="z-10 flex h-6 w-6 shrink-0 items-center justify-center rounded-full bg-blue-100 ring-0 ring-white dark:bg-blue-900 dark:ring-gray-900 sm:ring-8"
				>
					<svg
						class="h-2.5 w-2.5 text-blue-800 dark:text-blue-300"
						aria-hidden="true"
						xmlns="http://www.w3.org/2000/svg"
						fill="currentColor"
						viewBox="0 0 20 20"
					>
						<path
							d="M20 4a2 2 0 0 0-2-2h-2V1a1 1 0 0 0-2 0v1h-3V1a1 1 0 0 0-2 0v1H6V1a1 1 0 0 0-2 0v1H2a2 2 0 0 0-2 2v2h20V4ZM0 18a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V8H0v10Zm5-8h10a1 1 0 0 1 0 2H5a1 1 0 0 1 0-2Z"
						/>
					</svg>
				</div>
				<div class="hidden h-0.5 w-full bg-gray-200 dark:bg-gray-700 sm:flex"></div>
			</div>
			<div class="mt-3 sm:pe-8">
				<h3 class="text-lg font-semibold text-gray-900 dark:text-white">
					Step 1 : Creating Account
				</h3>
				<p class="text-base font-normal text-gray-500 dark:text-gray-400">
					Click on the Create Account button on the top of the page
				</p>
			</div>
		</li>
		<li class="relative mb-6 sm:mb-0 md:w-1/3">
			<div class="flex items-center">
				<div
					class="z-10 flex h-6 w-6 shrink-0 items-center justify-center rounded-full bg-blue-100 ring-0 ring-white dark:bg-blue-900 dark:ring-gray-900 sm:ring-8"
				>
					<svg
						class="h-2.5 w-2.5 text-blue-800 dark:text-blue-300"
						aria-hidden="true"
						xmlns="http://www.w3.org/2000/svg"
						fill="currentColor"
						viewBox="0 0 20 20"
					>
						<path
							d="M20 4a2 2 0 0 0-2-2h-2V1a1 1 0 0 0-2 0v1h-3V1a1 1 0 0 0-2 0v1H6V1a1 1 0 0 0-2 0v1H2a2 2 0 0 0-2 2v2h20V4ZM0 18a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V8H0v10Zm5-8h10a1 1 0 0 1 0 2H5a1 1 0 0 1 0-2Z"
						/>
					</svg>
				</div>
				<div class="hidden h-0.5 w-full bg-gray-200 dark:bg-gray-700 sm:flex"></div>
			</div>
			<div class="mt-3 sm:pe-8">
				<h3 class="text-lg font-semibold text-gray-900 dark:text-white">Step 2 : Fill the Form</h3>
				<p class="text-base font-normal text-gray-500 dark:text-gray-400">
					Fill up the sign up form using your real details and mobile numbers which are in use. <button
						on:click={toggleModal}
						class="underline">Click Here</button
					> to get to the application
				</p>
			</div>
		</li>

		<li class="relative mb-6 sm:mb-0 md:w-1/3">
			<div class="flex items-center">
				<div
					class="z-10 flex h-6 w-6 shrink-0 items-center justify-center rounded-full bg-blue-100 ring-0 ring-white dark:bg-blue-900 dark:ring-gray-900 sm:ring-8"
				>
					<svg
						class="h-2.5 w-2.5 text-blue-800 dark:text-blue-300"
						aria-hidden="true"
						xmlns="http://www.w3.org/2000/svg"
						fill="currentColor"
						viewBox="0 0 20 20"
					>
						<path
							d="M20 4a2 2 0 0 0-2-2h-2V1a1 1 0 0 0-2 0v1h-3V1a1 1 0 0 0-2 0v1H6V1a1 1 0 0 0-2 0v1H2a2 2 0 0 0-2 2v2h20V4ZM0 18a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V8H0v10Zm5-8h10a1 1 0 0 1 0 2H5a1 1 0 0 1 0-2Z"
						/>
					</svg>
				</div>
				<div class="hidden h-0.5 w-full bg-gray-200 dark:bg-gray-700 sm:flex"></div>
			</div>
			<div class="mt-3 sm:pe-8">
				<h3 class="text-lg font-semibold text-gray-900 dark:text-white">Step 3 : Approval</h3>
				<p class="text-base font-normal text-gray-500 dark:text-gray-400">
					Wait until we reveiw your request and send the approval to your email inbox
				</p>
			</div>
		</li>
	</ol>
</div>

<!-- Security -->

<div class="bg-gradient-to-br from-slate-300 to-slate-500 px-4 py-32">
	<Section name="cta">
		<Cta ctatype="heading">
			<h2 class="text-4xl font-bold text-white">Security</h2>
			<p class="mb-6 font-light text-white md:text-lg">
				At our online payment platform, security is our top priority. We use state-of-the-art
				encryption technology to protect your personal and financial information, and we comply with
				all industry standards for online security. You can feel confident that your information is
				safe with us.
			</p>
		</Cta>
	</Section>
</div>

<!-- Go Global -->

<div class="flex min-h-screen flex-col items-center justify-center gap-4 p-4">
	<h2 class="text-4xl font-bold text-black">Go Global With Wavelink</h2>
	<p class="mb-6 max-w-3xl text-center font-light text-black md:text-lg">
		A comprehensive platform designed to meet the needs of today's cross-border seller. Pay from any
		of the world's, into leading marketplaces, pay your suppliers and manage multiple stores from a
		single location. Access working capital to reinvest in your business and withdraw earnings in
		your home currency at low interest rates.
	</p>
	<div class="flex flex-row gap-4">
		<Card
			href="#"
			horizontal
			size="md"
			img="https://unsplash.com/photos/RJQE64NmC_o/download?ixid=M3wxMjA3fDB8MXxzZWFyY2h8M3x8Y3JlZGl0JTIwY2FyZHxlbnwwfHx8fDE3MDY3NzIxMjF8MA&force=true&w=640"
		>
			<h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
				Debit Cards & Credit Cards
			</h5>
			<p class="font-normal leading-tight text-gray-700 dark:text-gray-400">
				Make a payment anywhere in the world with any Visa and Mastercard.
			</p>
		</Card>
		<Card
			href="#"
			horizontal
			size="md"
			img="https://unsplash.com/photos/5kApSEYgMqw/download?ixid=M3wxMjA3fDB8MXxzZWFyY2h8MTR8fGNyeXB0byUyMGZpYXR8ZW58MHx8fHwxNzA2ODA0MzU3fDA&force=true&w=640"
		>
			<h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
				Crypto to Fiat
			</h5>
			<p class="font-normal leading-tight text-gray-700 dark:text-gray-400">
				Convert your digital assets into any currency of your choice to pay your bills, shopping, or
				cashing out from cryptocurrency investments.
			</p>
		</Card>
	</div>
</div>

<!-- Pricing -->

<div id="pricing" class="flex min-h-screen items-center justify-center">
	<Card
		img="https://unsplash.com/photos/hpjSkU2UYSU/download?ixid=M3wxMjA3fDB8MXxzZWFyY2h8MzJ8fGNoYXJ0fGVufDB8fHx8MTcwNjc4ODAyNXww&force=true&w=640"
		size="md"
	>
		<h5 class="mb-2 text-center text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
			Pricing
		</h5>
		<p>International Rates Will be at <strong>5%</strong></p>
		<p>Domestic Rates Will Start From <strong>2.5%</strong></p>
		<div class="flex w-full items-center justify-center pt-4">
			<Button class="w-fit" on:click={toggleModal}>
				Create an Account <ArrowRightOutline class="ms-2 h-3.5 w-3.5 text-white" />
			</Button>
		</div>
	</Card>
</div>

<!-- Signup Form -->
<Modal title="Sign Up Form" bind:open={defaultModal} {dismissable} class="min-w-full">
	<form on:submit={onSubmit}>
		<input type="hidden" name="_email.subject" value="Wave-Link Registration Information" />
		<input type="hidden" name="_email.from" value="Wave-Link Pay" />
		<input type="hidden" name="_feedback.whitelabel" value="true" />
		<input
			type="hidden"
			name="_feedback.success.title"
			value="Your Application has been submitted successfully"
		/>
		{#if errorMessage}
			<Alert color="red" class="mb-4">
				<InfoCircleSolid slot="icon" class="h-4 w-4" />
				<span class="font-medium">Error!</span>
				{errorMessage}
			</Alert>
		{/if}
		{#if showAll}
			<h2 class="mb-4 text-2xl font-semibold">Review Your Form</h2>
		{/if}
		{#if slide === 1 || showAll}
			<div class="mb-4 grid grid-cols-1 gap-4 md:grid-cols-2">
				<div>
					<Label>
						Select the area of Operations
						<Select class="mt-2" bind:value={data.geoArea} items={countries} required />
						<input type="hidden" name="GeoLocation" value={data.geoArea} />
					</Label>
				</div>
				<div class=" col-span-2">
					<p class="mb-5 text-gray-900 dark:text-white">Accept Payments with Euro Exim Bank As</p>
					<div class="grid w-full gap-6 md:grid-cols-2">
						<Radio
							name="Payment Type"
							value="Individual"
							bind:group={data.paymentType}
							custom
							required
						>
							<div
								class="inline-flex h-full w-full cursor-pointer items-center justify-between rounded-lg border border-gray-200 bg-white p-5 text-gray-500 hover:bg-gray-100 hover:text-gray-600 peer-checked:border-primary-600 peer-checked:text-primary-600 dark:border-gray-700 dark:bg-gray-800 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-gray-300 dark:peer-checked:text-primary-500"
							>
								<div class="block">
									<div class="w-full text-lg font-semibold">An Individual</div>
									<div class="w-full">For freelanceres, sole traders and unregistered business</div>
								</div>
								<ArrowRightOutline class="ms-3 h-6 w-6" />
							</div>
						</Radio>
						<Radio
							name="Payment Type"
							value="Business"
							bind:group={data.paymentType}
							custom
							required
						>
							<div
								class="inline-flex h-full w-full cursor-pointer items-center justify-between rounded-lg border border-gray-200 bg-white p-5 text-gray-500 hover:bg-gray-100 hover:text-gray-600 peer-checked:border-primary-600 peer-checked:text-primary-600 dark:border-gray-700 dark:bg-gray-800 dark:text-gray-400 dark:hover:bg-gray-700 dark:hover:text-gray-300 dark:peer-checked:text-primary-500"
							>
								<div class="block">
									<div class="w-full text-lg font-semibold">
										As a registered business, non-profit or NGO
									</div>
									<div class="w-full">
										Your Business is registered and you have a Business Bank Account
									</div>
								</div>
								<ArrowRightOutline class="ms-3 h-6 w-6" />
							</div>
						</Radio>
					</div>
				</div>
			</div>
		{/if}
		{#if slide === 2 || showAll}
			<h2 class="mb-4 text-2xl font-semibold">Personal Information (2/4)</h2>
			<div class="mb-4 grid grid-cols-1 gap-4 md:grid-cols-2">
				<div>
					<Label for="Full Name" class="mb-2">Full Name</Label>
					<Input
						type="text"
						id="Full Name"
						placeholder="John Doe"
						bind:value={data.fullName}
						required
					/>
				</div>
				<div>
					<Label for="Email" class="mb-2">Email Address</Label>
					<Input
						type="email"
						id="Email"
						placeholder="Someone@email.com"
						bind:value={data.email}
						required
					/>
				</div>
				<div>
					<Label for="Country" class="mb-2">What Country Are You From?</Label>
					<Input
						type="text"
						id="Country"
						placeholder="United States"
						bind:value={data.country}
						required
					/>
				</div>
				<div>
					<Label for="State" class="mb-2">Which State are you based on?</Label>
					<Input type="text" id="State" placeholder="New York" bind:value={data.state} required />
				</div>
				<div>
					<Label for="City" class="mb-2">What City are you based on?</Label>
					<Input
						type="text"
						id="City"
						placeholder="New York City"
						bind:value={data.city}
						required
					/>
				</div>
				<div>
					<Label for="ZIP Code" class="mb-2">What is your PIN / ZIP Code?</Label>
					<Input type="text" id="ZIP Code" placeholder="10001" bind:value={data.zip} required />
				</div>
				<div>
					<Label for="phone" class="mb-2">Enter Your Mobile Number</Label>
					<Input type="tel" id="phone" placeholder="123-456-789" bind:value={data.phone} required />
				</div>
			</div>
		{/if}
		{#if slide === 3 || showAll}
			<h2 class="mb-4 text-2xl font-semibold">Business Information (3/4)</h2>
			<div class="mb-4 grid grid-cols-1 gap-4 md:grid-cols-2">
				<div>
					<Label for="Business Name" class="mb-2">Business Name</Label>
					<Input
						type="text"
						id="Business Name"
						placeholder="John Doe"
						bind:value={data.businessName}
						required
					/>
				</div>
				<div>
					<Label for="Registered Address" class="mb-2">Registered Address</Label>
					<Input
						type="text"
						id="Registered Address"
						placeholder="123, 5th Avenue"
						bind:value={data.registeredAddress}
						required
					/>
				</div>
				<div>
					<Label for="Business Address" class="mb-2">Business Address</Label>
					<Input
						type="text"
						id="Business Address"
						placeholder="123, 5th Avenue"
						bind:value={data.businessAddress}
						required
					/>
				</div>
				<div>
					<Label for="Website URL" class="mb-2">Website URL</Label>
					<Input
						type="url"
						id="Website URL"
						placeholder="https://www.example.com"
						bind:value={data.websiteURL}
						required
					/>
				</div>
			</div>
		{/if}
		{#if slide === 4 || showAll}
			<h2 class="mb-4 text-2xl font-semibold">Business Description (4/4)</h2>
			<div class="mb-4">
				<Label for="Business Description" class="mb-2">Business Description</Label>
				<Textarea
					id="Business Description"
					placeholder="Describe your business in a few words"
					bind:value={data.businessDescription}
					required
				/>
			</div>
			<div class="mb-4">
				<Label for="Your Role" class="mb-2">Your Role</Label>
				<Select class="mt-2" bind:value={data.yourRole} items={roles} required />
			</div>
			{#if data.yourRole === 'Other'}
				<div class="mb-4">
					<Label for="Other Role" class="mb-2">Please Enter Your Role</Label>
					<Input
						type="text"
						id="Other Role"
						placeholder="Freelancer"
						bind:value={data.otherRole}
						required
					/>
				</div>
			{/if}
		{/if}
		{#if slide === 104}
			<div class="mb-4">
				<Alert color="red">
					<InfoCircleSolid slot="icon" class="h-4 w-4" />
					<span class="font-medium">Error!</span>
					{errorMessage}
				</Alert>
			</div>
		{/if}
		{#if slide === 200}
			<div class="mb-4">
				<Alert color="green">
					<InfoCircleSolid slot="icon" class="h-4 w-4" />
					<span class="font-medium">Success!</span>
					Your application has been submitted successfully
				</Alert>
			</div>
		{/if}
		{#if slide < 100}
			<div class="mt-8 flex w-full flex-row justify-between">
				<Button color="alternative" on:click={prevSlide}>Previous</Button>
				{#if slide === 5}
					<Button type="submit">Submit</Button>
				{/if}
				{#if slide < 5}
					<Button on:click={nextSlide}>Next</Button>
				{/if}
			</div>
		{/if}
	</form>
</Modal>
