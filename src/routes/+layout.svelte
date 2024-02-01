<script>
	import '../app.pcss';
    import { Navbar, NavBrand, NavLi, NavUl, NavHamburger } from 'flowbite-svelte';
</script>

<Navbar  >
  <NavBrand href="/">
    <img src="/navicon.png" class="me-3 h-6 sm:h-9" alt="Wavelink Pay Logo" />
    <span class="self-center whitespace-nowrap text-xl font-semibold dark:text-white">WAVE-LINK</span>
  </NavBrand>
  <NavHamburger  />
  <NavUl >
    <NavLi href="/">Home</NavLi>
    <NavLi href="/about">About</NavLi>
    <NavLi href="/docs/components/navbar">Navbar</NavLi>
    <NavLi href="/pricing">Pricing</NavLi>
    <NavLi href="/contact">Contact</NavLi>
    <NavLi href="/signup">Sign Up</NavLi>
  </NavUl>
</Navbar>

<slot />
