<script>
	import Nav from '$lib/nav.svelte';
	import '../app.css'
</script>

<Nav />

<main class="container max-w-4xl mx-auto px-4">
	<slot />
</main>
