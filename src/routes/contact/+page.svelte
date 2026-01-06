<script lang="ts">
	import type { ContactContent } from './+page';

	let { data } = $props();

	const { Content } = data as ContactContent;
</script>

<section class="section">
	<div class="title">Contact</div>
</section>

<section class="section">
	<div class="container">
		<Content />
	</div>
</section>

<style>
</style>
