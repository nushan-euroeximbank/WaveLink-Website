<script>
	import {
		Section,
		News,
		HeroHeader,
		FeatureDefault,
		FeatureItem,
		Cta
	} from 'flowbite-svelte-blocks';
	import { Button, Card } from 'flowbite-svelte';
	import {
		ArrowRightSolid,
		ArrowRightOutline,
		VideoSolid,
		ChartSolid,
		LandmarkSolid,
		BriefcaseSolid,
		DollarSolid,
		RocketSolid
	} from 'flowbite-svelte-icons';
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
			<a href="/signup">
				<Button size="lg">
					Join Today <ArrowRightSolid size="md" class="-mr-1 ml-2" />
				</Button>
			</a>
			<a href="/">
				<!-- <Button size="lg" color="light">
					<VideoSolid size="xs" class="-ml-1 mr-2" />
					Watch video
				</Button>
			</a> -->
			</a>
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
					><LandmarkSolid class="text-primary-600 dark:text-primary-300" /></svelte:fragment
				>
				<svelte:fragment slot="h3">No Currency Fee</svelte:fragment>
				<svelte:fragment slot="paragraph"
					>Receive money from all over the world without currency fees</svelte:fragment
				>
			</FeatureItem>
			<FeatureItem>
				<svelte:fragment slot="icon"
					><BriefcaseSolid class="text-primary-600 dark:text-primary-300" /></svelte:fragment
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
					><RocketSolid class="text-primary-600 dark:text-primary-300" /></svelte:fragment
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
			<a
				href="/signup"
				class="inline-flex items-center rounded-lg bg-primary-700 px-5 py-2.5 text-center text-sm font-medium text-white hover:bg-primary-800 focus:ring-4 focus:ring-primary-300 dark:focus:ring-primary-900"
			>
				Get started
				<ArrowRightSolid size="md" class="-mr-1 ml-2" />
			</a>
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
					Fill up the sign up form using your real details and mobile numbers which are in use. <a
						href="/signup"
						class="underline">Click Here</a
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
			<Button class="w-fit" href="/signup">
				Create an Account <ArrowRightOutline class="ms-2 h-3.5 w-3.5 text-white" />
			</Button>
		</div>
	</Card>
</div>
