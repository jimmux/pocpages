<script lang="ts">
	import { Heading, P } from 'flowbite-svelte';
import type { ContactContent } from './+page';

	let { data } = $props();

	const { Content } = data as ContactContent;
</script>

<section>
	<Heading>Contact</Heading>
</section>

<section>
	<P>
		<Content />
	</P>
</section>
