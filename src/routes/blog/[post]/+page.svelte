<script lang="ts">
	import type { BlogPost } from './+page';
	import { showDate } from '$lib/utils';

	let { data } = $props();

	const { title, date, author, Content } = data as BlogPost;

	let prettyDate = $derived(showDate(date));
</script>

<article class="container">
	<section class="section">
		<div class="title">
			{title}
		</div>
		<div class="subtitle">
			{prettyDate}
		</div>
		<div class="block is-italic">
			{author}
		</div>
	</section>
	<section class="section">
		<Content />
	</section>
</article>

<style>
</style>
