<script lang="ts">
	import { setContext, onMount } from 'svelte';
	import branding from '$lib/assets/branding.png';
  import { fade } from 'svelte/transition';

  // Useful for showing a reminder for clients hitting the preview site
  const OFFICIAL_URL = "https://actual.pages.dev";

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

<template lang="pug">
  svelte:head
    title POCPages template site
    meta(property="og:title" content="POCPages template site")

  nav.navbar(aria-label="main navigation")
    .navbar-brand
      a.navbar-item(href="/")
        img(src!="{branding}" alt="Home Page")
      a.navbar-burger(
        onclick!="{toggleBurger}"
        class:is-active!="{showMenu}"
        role="button" 
        aria-label="menu" 
        aria-expandable="false"
      )
        span(aria-hidden="true")
        span(aria-hidden="true")
        span(aria-hidden="true")
        span(aria-hidden="true")

    .navbar-menu(class:is-active!="{showMenu}")
      .navbar-start
        a.navbar-item(href="/blog") Blog
        a.navbar-item(href="/contact") Contact

  //- Page transition effect
  +key("data.currentRoute")
    main.inner(in:fade!="{{ duration: 150, delay: 150 }}" out:fade!="{{ duration: 150 }}")
      | {@render children()}

  .footer 
    .container
      .has-text-centered Copyright© {getCopyrightYear()}

  //- Warning modal for preview site
  .modal(class:is-active!="{showPreviewModal}")
    .modal-background
    .modal-content
      .card
        .card-content
          .block.has-text-centered
            | Your are viewing an in-development preview.
          .level
            .level-item
              .button(onclick!="{goToOfficialSite}")
                | Go to the official site
            .level-item
              .button(onclick!="{hidePreviewModal}")
                | Continue to the preview site
</template>

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
