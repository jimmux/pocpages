<script lang="ts">
</script>

<template lang="pug">
  section.hero.is-fullheight.bg-aurora-trails
    .hero-body
      .container.has-text-centered
        .title.font-branded POC Pages
        .subtitle Useful, quick
    
    .container
      .title Useful bits
      .columns
        .column
          .box.is-primary
            .subtitle SvelteKit
            .block.
              Built on Vite, so it's quick and sensible by default.
            .block.
              Svelte itself is an uncomplicated way to do functional composition for the web.
        .column
          .box
            .subtitle Pug templates
            .block.
              XML is clunky, why are we still writing our DOMs in it?
      .columns
        .column
          .box
            .subtitle PagesCMS + Markdown
            .block.
              Simple but effective.
        .column
          .box
            .subtitle Bulma
            .block.
              Easy to use CSS classes, with minimal implementation details.
        .column
          .box
            .subtitle TypeScript
            .block.
              Of course.

</template>

<style>
	.bg-aurora-trails {
		background-image: url('$lib/assets/stacked.jpg');
		background-attachment: fixed;
		background-size: cover;
		background-position-x: center;
		background-position-y: top;
		min-height: 70vh;
	}

	.font-branded {
		font-family: var(--custom-font-branded);
	}
</style>
