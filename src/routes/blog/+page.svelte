<script lang="ts">
	import { showDate } from '$lib/utils';

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

<section class="section">
	<div class="title">Blog</div>
</section>

<section class="section">
	<ul class="container">
		{#each prettyData.posts as post}
			<li class="block">
				<a class="subtitle" href={post.path}>
					{post.meta.title}
				</a>
				<p class="is-italic">
					Published {post.meta.date}
				</p>
			</li>
		{/each}
	</ul>
</section>

<style>
</style>
