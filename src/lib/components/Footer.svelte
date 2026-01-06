<script lang="ts">
	import { P } from "flowbite-svelte";

	let props = $props();

	function getCopyrightYear(): string {
		return new Date(Date.now()).getFullYear().toString();
	}
</script>

<footer {...props}>
	<P size="sm" class="text-center pb-6">Copyright© {getCopyrightYear()}</P>
</footer>
