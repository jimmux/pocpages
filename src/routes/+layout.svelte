<script lang="ts">
	import { setContext, onMount } from 'svelte';
	import branding from '$lib/assets/branding.png';
	import { fade } from 'svelte/transition';

	// Useful for showing a reminder for clients hitting the preview site
	const OFFICIAL_URL = 'https://actual.pages.dev';

	let { children, data } = $props();
	let showMenu = $state<boolean>(false);
	let showPreviewModal = $state<boolean>(false);

	function toggleBurger() {
		showMenu = !showMenu;
	}

	setContext('iconCtx', {
		size: '20' // Global Ionicon size in pixels
	});

	function getCopyrightYear(): string {
		return new Date(Date.now()).getFullYear().toString();
	}

	function hidePreviewModal(): void {
		showPreviewModal = false;
	}

	function goToOfficialSite(): void {
		window.location.href = OFFICIAL_URL;
	}

	onMount(() => {
		showPreviewModal = !window.location.href.includes(OFFICIAL_URL);
	});
</script>

<svelte:head>
	<title>POCPages template site</title>
	<meta property="og:title" content="POCPages template site" />
</svelte:head>

<nav class="navbar" aria-label="main navigation">
	<div class="navbar-brand">
		<a class="navbar-item" href="/">
			<img src={branding} alt="Home Page" />
		</a>
		<a
			class="navbar-burger"
			onclick={toggleBurger}
			class:is-active={showMenu}
			role="button"
			aria-label="menu"
			aria-expandable="false"
		>
			<span aria-hidden="true"></span>
			<span aria-hidden="true"></span>
			<span aria-hidden="true"></span>
			<span aria-hidden="true"></span>
		</a>
	</div>

	<div class="navbar-menu" class:is-active={showMenu}>
		<div class="navbar-start">
			<a class="navbar-item" href="/blog">Blog</a>
			<a class="navbar-item" href="/contact">Contact</a>
		</div>
	</div>
</nav>

<!-- Page transition effect -->
{#key data.currentRoute}
	<main class="inner" in:fade={{ duration: 150, delay: 150 }} out:fade={{ duration: 150 }}>
		{@render children()}
	</main>
{/key}

<div class="footer">
	<div class="container">
		<div class="has-text-centered">
			Copyright© {getCopyrightYear()}
		</div>
	</div>
</div>

<!-- Warning modal for preview site -->
<div class="modal" class:is-active={showPreviewModal}>
	<div class="modal-background"></div>
	<div class="modal-content">
		<div class="card">
			<div class="card-content">
				<div class="block has-text-centered">Your are viewing an in-development preview.</div>
				<div class="level">
					<div class="level-item"></div>
					<div class="button" onclick={goToOfficialSite}>Go to the official site</div>
					<div class="level-item">
						<div class="button" onclick={hidePreviewModal}>Continue to the preview site</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</div>

<style>
	/* From https://fonts.google.com/selection/embed */
	@import url('https://fonts.googleapis.com/css2?family=Aboreto&display=swap');

	@import 'https://cdn.jsdelivr.net/npm/bulma@1.0.2/css/bulma.min.css';

	:root {
		/* As per https://bulma.io/documentation/helpers/color-helpers/ */
		--bulma-family-secondary: 'Aboreto', serif;
		--bulma-primary-h: 50deg;
		--bulma-primary-l: 80%;
		--custom-font-branded: 'Aboreto', serif;
		--custom-overlay: hsl(0, 0%, 100%, 70%);
		--bulma-link-h: 36deg;
		--bulma-link-s: 75%;
		--bulma-link-l: 50%;
	}

	.inner {
		min-height: 90vh;
	}
</style>
