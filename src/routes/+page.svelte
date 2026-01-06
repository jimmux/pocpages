<script lang="ts">
	import { Card, Heading, P } from "flowbite-svelte";

	const bits = [
		{
			title: "SvelteKit",
			text: [
				"Built on Vite, so it's quick and sensible by default.",
				"Svelte itself is an uncomplicated way to do functional composition for the web."
			]
		},
		{
			title: "PagesCMS + Markdown",
			text: [
				"Simple but effective content management, for easy collaboration."
				]
		},
		{
			title: "Flowbite Svelte componewnt library",
			text: [
				"Works well with Tailwind, easy to adjust, doesn't get in the way, good-enough defaults.",
				"It provides enough for rapid development while not getting in the way."
			]
		},
		{
			title: "TypeScript",
			text: [
				"Of course."
			]
		},
	];
</script>

<section class="is-fullheight bg-aurora-trails">
	
	<div class="text-center">
		<Heading tag="h1">POC Pages</Heading>
		<Heading tag="h2">Useful, quick</Heading>
	</div>

	<div>
		<h3>Useful bits</h3>

		<div class="grid grid-cols-3 gap-4">
			{#each bits as bit}
				<Card class="p-6">
					<Heading tag="h3" class="mb-4">
						{bit.title}
					</Heading>
					{#each bit.text as text }
						<P>
							{text}
						</P>
					{/each}
				</Card>
			{/each}
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
</style>
