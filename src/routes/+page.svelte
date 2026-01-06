<script lang="ts">
</script>

<section class="hero is-fullheight bg-aurora-trails">
	<div class="hero-body">
		<div class="container has-text-centered">
			<div class="title font-branded">POC Pages</div>
			<div class="subtitle">Useful, quick</div>
		</div>
	</div>

	<div class="container">
		<div class="title">Useful bits</div>
		<div class="columns">
			<div class="column">
				<div class="box is-primary">
					<div class="subtitle">SvelteKit</div>
					<div class="block">Built on Vite, so it's quick and sensible by default.</div>
					<div class="block">
						Svelte itself is an uncomplicated way to do functional composition for the web.
					</div>
				</div>
			</div>
		</div>
		<div class="columns">
			<div class="column">
				<div class="box">
					<div class="subtitle">PagesCMS + Markdown</div>
					<div class="block">Simple but effective.</div>
				</div>
			</div>

			<div class="column">
				<div class="box">
					<div class="subtitle">Bulma</div>
					<div class="block">Easy to use CSS classes, with minimal implementation details.</div>
				</div>
			</div>

			<div class="column">
				<div class="box">
					<div class="subtitle">TypeScript</div>
					<div class="block">Of course.</div>
				</div>
			</div>
		</div>
	</div>
</section>

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
