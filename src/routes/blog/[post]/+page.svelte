<script lang="ts">
	import type { BlogPost } from './+page';
	import { showDate } from '$lib/utils';
	import { Heading, P } from 'flowbite-svelte';

	let { data } = $props();

	const { title, date, author, Content } = data as BlogPost;

	let prettyDate = $derived(showDate(date));
</script>

<article>
	<section>
		<Heading>
			{title}
		</Heading>
		<Heading tag="h4">
			{prettyDate}
		</Heading>
		<Heading tag="h5">
			{author}
		</Heading>
	</section>
	<section>
		<P>
			<Content />
		</P>
	</section>
</article>

<style>
</style>
