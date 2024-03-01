<script lang="ts">
	import Card from '$lib/Card.svelte';
	import Countdown from '$lib/Countdown.svelte';
	import InfoSection from '$lib/InfoSection.svelte';
</script>

<main class="p-12 flex-1">
	<section class="space-y-8 flex flex-col items-center w-full">
		<h1 class="text-6xl text-center font-bold caveat">Dante & Amanda</h1>
		<h2 class="text-4xl text-center caveat">Västbyn 31/8 2024</h2>
		<img src="par.jpeg" alt="Dante & Amanda" class="rounded-lg md:max-w-[600px] w-96" />
		<Countdown
			from="2024-08-31 15:00:00"
			dateFormat="YYYY-MM-DD H:m:s"
			zone="Europe/Stockholm"
			let:remaining
		>
			<div class="countdown w-full pt-8">
				{#if remaining.done === false}
					<p><span>{remaining.days}</span> dagar</p>
					<p><span>{remaining.hours}</span> timmar</p>
					<p><span>{remaining.minutes}</span> minuter</p>
					<p><span>{remaining.seconds}</span> sekunder</p>
				{:else}
					<h2>Nu händer det!</h2>
				{/if}
			</div>
		</Countdown>
	</section>
	<section class="mt-32 max-w-[920px] m-auto">
		<InfoSection place="Västbyn 22, Robertsfors, Sweden" imgSrc="vigsel.png">
			<h2 class="text-4xl caveat mb-8">15.00 - Vigsel i Västbyn</h2>
			<p>
				Klockan tre börjar vår vigsel hemma på gården i Västbyn. Du hittar smidigast dit genom att
				följa E4:an norrut från Umeå, svänga av i Sikeå mot Robertsfors väg 651. Efter Överklinten,
				håll utkik efter Västbyn skylten, ta höger och följ vägen fram till Västbyn 22, finns skylt
				på gårdshuset.
			</p>
			<p class="mt-2">
				<b>
					<a
						href="https://www.google.com/maps/place/V%C3%84STBYN+22,+915+91+Robertsfors,+Sweden/@64.253835,20.6367,9z/data=!4m6!3m5!1s0x467c248891f339f9:0x723c5abeb8aab763!8m2!3d64.2538352!4d20.6366997!16s%2Fg%2F11c0_fh_w3?hl=en-GB&entry=ttu"
						>Address: Västbyn 22, 91591, Robertsfors.</a
					>
				</b>
			</p>
		</InfoSection>
		<InfoSection
			place="Folkets Hus, Robertsfors, Sweden"
			imgSrc="middag.png"
			name="Middag och Fest"
			id="fest"
		>
			<h2 class="text-4xl caveat mb-8">ca 17.00 - Middag och Fest i Folkets Hus</h2>
			<p>
				Runt 17 planeras bröllopsparet anlända till "Folkan". Väl där är det middag med påföljande
				fest. Från Västbyn till Folkets Hus är det ungefär 2,5 kilometer. Ta gärna följe med någon
				som hittar i trakten, annars hittar man rätt med adressen nedan. Det är alltid utför och
				medvind till Folkan så en medhavd cykel är kanske ett trevligt alternativ?
			</p>
			<p class="mt-2">
				<b>
					<a
						target="_blank"
						rel="noopener"
						aria-label="Address to Folkets Hus"
						href="https://www.google.com/maps/place/Overklinten+Folketshus/@64.247912,20.628858,13z/data=!4m6!3m5!1s0x467c25e8fd3b9089:0x27586e54634bee0f!8m2!3d64.2473896!4d20.6596278!16s%2Fg%2F11hstsztwf?hl=en-GB&entry=ttu"
						>Address: Kvarnvägen 11, 91591, Robertsfors.</a
					>
				</b>
			</p></InfoSection
		>

		<h1 class="text-6xl text-center font-bold caveat mb-8">Bra att Veta</h1>

		<section class="mb-32 grid md:grid-cols-2 gap-10" id="bra">
			<!-- First item -->
			<Card
				title="Mat och dryck"
				content="I samband med brudskål serveras det bubbel och snittar. Till middagen kommer det att dukas upp till buffe och påföljande efterrätt. Vi bjuder på två glas dryck under middagen. Baren kommer vara öppen till självkostnadspris under kvällen."
				imgSrc="matochdryck.webp"
				alt="Table setup for an event"
				id="mat"
			/>

			<!-- Second item -->

			<Card title="Boende" imgSrc="kvarn.png" alt="City view" id="boende">
				<p>
					Om du vill övernatta finns det olika alternativ. Har du husvagn, husbil eller tält så
					finns det många fina platser i närheten (hör av dig om du vill ha tips). Vill du bo mer
					bekvämt rekommenderar vi hotell Överklintens kvarn som ligger ett stenkast från
					festlokalen. Hela kvarnen är reserverad till bröllopsgäster, finns begränsat antal rum.
				</p>
				<p>
					Mer information hittar ni här:
					<a href="http://www.overklintenskvarn.se/" target="_blank" rel="noopener"
						>Överklintens kvarn</a
					>.
				</p>
				<p>
					Fler boendealternativ hittar du på:
					<a href="https://www.visitrobertsfors.nu/sv/bo">Visit Robertsfors</a>.
				</p>
			</Card>
			<!-- Third item -->
			<Card
				title="Klädsel"
				content="Ett förslag är kavaj för herrar. Val av färg både på kavajen och skjortan gör du själv. För damer kan ju klänning, kjol, byxdress eller dräkt vara passande.
        Men oavsett är det viktiga att du känner dig bekväm och fin."
				imgSrc="kladsel.webp"
				alt="Dress code demonstration"
				id="kladsel"
			/>

			<Card
				title="Barn"
				content="Era barn är naturligtvis välkomna på vigseln och under middagen, efter 20:00 har vi planerat att dansgolvet öppnas och då tänker vi att det är dags för barnen att avlägsna sig. Spädbarn är självklart välkomna under hela firandet."
				imgSrc="barn.webp"
				alt="Children at an event"
				id="barn"
			/>
		</section>

		<h1 id="onskelista" class="text-6xl text-center font-bold caveat mb-8">Önskelista</h1>
		<section class="mb-32 shadow-xl p-12 bg-white">
			<p>
				Din närvaro är allt vi önskar. Men vill ni ändå uppmärksamma vår dag med en gåva är ett
				bidrag till vår bröllopsresa en uppskattad gåva, swisha till 070-3229775.
			</p>
		</section>

		<h1 id="osa" class="text-6xl text-center font-bold caveat mb-8">Tal</h1>
		<section class="mb-32 space-y-4 shadow-xl p-12 bg-white">
			<p>
				Om du vill hålla tal, uppträda eller spexa får du gärna anmäla det nedan. Vi ser inte
				anmälan utan informationen skickas direkt till våra toastmasters Anne och [TODO].
			</p>

			<p>För tal brukar ca 5 minuter vara lagom.</p>
			<p>Har du frågor om tal och spex kan du mejla eller ringa våra toastmasters.</p>
			<p><b>Anne Larsen</b> 070-296 69 31</p>
		</section>
		<h1 class="text-6xl text-center font-bold caveat mb-8">OSA</h1>
		<section class="mb-32 space-y-4 shadow-xl p-12 bg-white">
			OSA i formuläret nedan senast den 1/7. Om du har frågor hör gärna av dig.
		</section>
	</section>
</main>

<style lang="postcss">
	:global(html) {
		background-color: theme(colors.gray.100);
	}

	.countdown {
		display: flex;
		justify-content: space-evenly;
		gap: 1rem;
	}

	.countdown p {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 2rem;
	}

	.countdown span {
		font-size: 3rem;
		font-weight: bold;
	}
</style>
