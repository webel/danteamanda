<script lang="ts">
	export let place = 'Västbyn 22, Robertsfors, Sweden';

	// create the place string for the url
	$: placeString = place.replace(/ /g, '+');
</script>

<div class="shadow-xl overflow-hidden resize-none max-w-full w-[300px] h-[430px]">
	<div id="embedded-map-display" style="height:100%; width:100%;max-width:100%;">
		<iframe
			style="height:100%;width:100%;border:0;"
			frameborder="0"
			src="https://www.google.com/maps/embed/v1/place?q={placeString}&zoom=9&key=AIzaSyBFw0Qbyq9zTFTd-tUY6dZWTgaQzuU17R8"
		></iframe>
	</div>
	<style>
		#embedded-map-display img.text-marker {
			max-width: none !important;
			background: none !important;
		}
		img {
			max-width: none;
		}
	</style>
</div>
