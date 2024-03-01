<script lang="ts">
	import Map from './Map.svelte';

	export let name = 'Vigsel';
	export let id = 'vigsel';
	export let place = 'Västbyn 22, Robertsfors, Sweden';
	export let imgSrc = 'vigsel.png';
</script>

<section class="space-y-8 mb-32" {id}>
	<h1 class="text-6xl text-center font-bold caveat">{name}</h1>
	<div class="flex flex-wrap items-center justify-center gap-8">
		<img src={imgSrc} alt="Vigsel" class="w-full shadow-xl lg:h-[430px] lg:w-auto" />
		<Map {place} />
	</div>
	<div class="shadow-xl p-12 bg-white">
		<slot />
	</div>
</section>
