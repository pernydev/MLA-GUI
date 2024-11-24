<script lang="ts">
	import Nav from '$lib/components/Nav.svelte';
	import '../app.css';
	let { children } = $props();
</script>

<div class="flex flex-col h-[100vh]">
	<Nav />
	{@render children()}
</div>
