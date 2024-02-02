<script>
	import '../app.pcss';
	import { Section } from 'flowbite-svelte-blocks';
	import {
		Navbar,
		NavBrand,
		NavLi,
		NavUl,
		NavHamburger,
		Footer,
		FooterBrand,
		FooterLinkGroup,
		FooterLink,
		FooterCopyright,
		FooterIcon
	} from 'flowbite-svelte';
</script>

<div class="fixed left-0 right-0 top-0 z-10">
	<Navbar>
		<NavBrand href="/">
			<img src="/navicon.png" class="me-3 h-6 sm:h-9" alt="Wavelink Pay Logo" />
			<span class="self-center whitespace-nowrap text-xl font-semibold dark:text-white"
				>WAVE-LINK</span
			>
		</NavBrand>
		<NavHamburger />
		<NavUl>
			<NavLi href="/">Home</NavLi>
			<NavLi href="/#pricing">Pricing</NavLi>
			<NavLi href="/signup">Sign Up</NavLi>
		</NavUl>
	</Navbar>
</div>

<slot />

<Footer footerType="socialmedia">
	<div class="mx-auto max-w-screen-xl text-center">
		<FooterBrand
			href="https://wavelinkpay.com"
			src="/navicon.png"
			alt="Wave-link Logo"
			name="Wave-Link Pay"
			aClass="flex justify-center items-center text-2xl font-semibold text-gray-900 dark:text-white"
		/>
		<p class="my-6 text-gray-500 dark:text-gray-400">
			A comprehensive platform designed to meet the needs of today's cross-border seller.
		</p>
		<FooterLinkGroup
			ulClass="flex flex-wrap justify-center items-center mb-6 text-gray-900 dark:text-white"
		>
			<FooterLink liClass="" aClass="mr-4 hover:underline md:mr-6" href="/">Home</FooterLink>
			<FooterLink liClass="" aClass="mr-4 hover:underline md:mr-6" href="/#pricing"
				>Pricing</FooterLink
			>
			<FooterLink liClass="" aClass="mr-4 hover:underline md:mr-6" href="/signup"
				>Sign Up</FooterLink
			>
			<!-- <FooterLink liClass="" aClass="mr-4 hover:underline md:mr-6" href="/">Blog</FooterLink>
			<FooterLink liClass="" aClass="mr-4 hover:underline md:mr-6" href="/"
				>Affiliate Program</FooterLink
			>
			<FooterLink liClass="" aClass="mr-4 hover:underline md:mr-6" href="/">FAQs</FooterLink>
			<FooterLink liClass="" aClass="mr-4 hover:underline md:mr-6" href="/">Contact</FooterLink> -->
		</FooterLinkGroup>
		<span class="text-sm text-gray-500 dark:text-gray-400 sm:text-center"
			>© 2024 <a href="https://wavelinkpay.com/" class="hover:underline">Wave-Link Pay</a>. All
			Rights Reserved.</span
		>
	</div>
</Footer>
