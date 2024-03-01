<script>
	import '../app.css';
	import Header from '$lib/Header.svelte';
</script>

<div class="min-h-screen bg-stone-100 md:flex flex-wrap">
	<Header />
	<slot />
</div>
