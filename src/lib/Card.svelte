<script lang="ts">
	export let title = 'Barn';
	export let content = 'Vi har valt att inte ha några barn på bröllopet.';
	export let imgSrc = 'barn.webp';
	export let alt = 'Children at an event';
	export let id = 'barn';
</script>

<div {id} class="space-y-2 shadow-xl bg-white">
	<img src={imgSrc} {alt} class="w-full object-cover" />
	<div class="px-8 py-6 pb-8">
		<h3 class="text-xl font-semibold mb-2 text-center">{title}</h3>
		{#if $$slots.default}
			<slot />
		{:else}
			<p>
				{content}
			</p>
		{/if}
	</div>
</div>
