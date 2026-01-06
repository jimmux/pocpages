<script lang="ts">
	import { Navbar, NavBrand, NavLi, NavUl, NavHamburger, DarkMode } from 'flowbite-svelte';

	export type NavLink = [label: string, href: string];

	interface Props {
		branding?: string;
		links?: NavLink[];
	}

	let { branding, links, ...props }: Props = $props();
</script>

<Navbar {...props}>
	<NavBrand href="/">
		<img src={branding} class="me-3 h-6 sm:h-9" alt="Logo" />
	</NavBrand>
	<div class="flex md:order-2">
		<DarkMode />
		<NavHamburger />
	</div>
	<NavUl class="order-1">
		{#each links as [label, href]}
			<NavLi {href}>{label}</NavLi>
		{/each}
	</NavUl>
</Navbar>
