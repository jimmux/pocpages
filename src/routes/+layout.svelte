<script lang="ts">
	import './layout.css';
	import { setContext } from 'svelte';
	import branding from '$lib/assets/branding.png';
	import { fade } from 'svelte/transition';
	import Footer from '$lib/components/Footer.svelte';
	import ModalDialog from '$lib/components/ModalDialog.svelte';
	import NavBar from '$lib/components/NavBar.svelte';
	import type { NavLink } from '$lib/components/NavBar.svelte';

	// Useful for showing a reminder for clients hitting the preview site
	const OFFICIAL_URL = 'https://actual.pages.dev';

	let { children, data } = $props();

	const links: NavLink[] = [
		["Home", "/"],
		["Blog", "/blog"],
		["Contact", "/contact"],
		["Examples", "/examples"]
	];

	setContext('iconCtx', {
		size: '20' // Global Ionicon size in pixels
	});

	function goToOfficialSite(): void {
		window.location.href = OFFICIAL_URL;
	}
</script>

<svelte:head>
	<title>POCPages template site</title>
	<meta property="og:title" content="POCPages template site" />
</svelte:head>

<div class="min-h-screen dark:bg-gray-900">

	<NavBar {links} {branding} class="dark:bg-gray-900"/>

	<!-- Page transition effect -->
	{#key data.currentRoute}
		<main in:fade={{ duration: 150, delay: 150 }} out:fade={{ duration: 150 }}>
			{@render children()}
		</main>
	{/key}

</div>

<Footer class="dark:bg-gray-900"/>

<!-- Warning modal for preview site -->
 <!-- TODO: depend on .env -->
<ModalDialog
  defaultOpen
  confirmText="Go to the official site" 
  cancelText="Continue to the preview site"
  onConfirm={goToOfficialSite}
>
  <div class="text-center">Your are viewing an in-development preview.</div>
</ModalDialog>

<style>

</style>
