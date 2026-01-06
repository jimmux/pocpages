<script lang="ts">
	import { showDate } from '$lib/utils';
	import { A, Heading, P } from 'flowbite-svelte';

	let { data } = $props();

	let prettyData = $derived({
		...data,
		posts: data.posts.map((post) => ({
			...post,
			meta: {
				...post.meta,
				date: showDate(post.meta.date)
			}
		}))
	});
</script>

<section>
	<Heading>Blog</Heading>
</section>

<section>
	<ul>
		{#each prettyData.posts as post}
			<li>
				<A href={post.path}>
					{post.meta.title}
				</A>
				<P>
					Published {post.meta.date}
				</P>
			</li>
		{/each}
	</ul>
</section>

<style>
</style>
