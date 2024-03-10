<script lang="ts">
	import clsx from 'clsx';
	import Card from '$lib/Card.svelte';
	import Countdown from '$lib/Countdown.svelte';
	import InfoSection from '$lib/InfoSection.svelte';
	import { speachesForm, osaForm } from '$lib/forms';
	import { page } from '$app/stores';
	import { goto } from '$app/navigation';
	import { onMount } from 'svelte';

	const currentLocation = $page.url.origin;

	let formParam = '';
	onMount(() => {
		formParam = $page.url.searchParams.get('form');

		if (formParam) {
			goto(`#${formParam}`);
		}
	});

	let numberOfOSA = 0;
	let showTal = false;
</script>

<main class="p-6 custom:p-12 flex-1">
	<section class="space-y-8 flex flex-col items-center w-full h-[calc(100vh-80px)] justify-center">
		<h1 class="text-6xl text-center font-bold la-luxes-script">Dante & Amanda</h1>
		<h2 class="text-5xl text-center la-luxes-script">Västbyn 31/8 2024</h2>
		<img
			src="start.jpg"
			alt="Dante & Amanda"
			class="rounded-lg w-80 md:w-[380px] custom:w-[500px]"
		/>
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
		<InfoSection place="Västbyn 22, Robertsfors, Sweden" imgSrc="par.jpeg">
			<h2 class="text-5xl la-luxes-script mb-8">15.00 - Vigsel i Västbyn</h2>
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
			place="Overklinten Folkets Hus, Robertsfors, Sweden"
			imgSrc="middag.jpg"
			name="Middag och Fest"
			id="fest"
		>
			<h2 class="text-5xl la-luxes-script mb-8">Middag och Fest i Folkets Hus</h2>
			<p>
				Efter vigseln blir det att ta sig till "Folkan". Väl där är det middag med påföljande fest.
				Från Västbyn till Folkets Hus är det ungefär 2,5 kilometer. Ta gärna följe med någon som
				hittar i trakten, annars hittar man rätt med adressen nedan.
			</p>
			<p class="mt-4">
				Det är alltid utför och medvind till Folkan så en medhavd cykel är kanske ett trevligt
				alternativ?
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

		<h1 id="bilder" class="text-6xl text-center font-bold la-luxes-script mb-8">Bilder</h1>
		<section class="mb-32 flex flex-col shadow-xl p-8 custom:p-12 bg-white">
			<p>
				Vi hoppas att ni är några i gästlistan som kan tänka sig att föreviga vår dag med bilder.
				Här kommer ni att kunna lägga upp bilder i en gemensam bildbank.
			</p>
			<button
				class="elegant-submit-button mx-auto mt-4"
				on:click={() =>
					window.open(
						'https://l.messenger.com/l.php?u=https%3A%2F%2Fphotos.app.goo.gl%2FWgKLAswaphfeE61y7&h=AT1jc1Ng4bp59Dy_iLU7z7y9a6VBdutGk4-piIJcJMMGu-Y-Bl02cJi0UounbUi2U4cfY3DTZpnfpp-MpwwpBESY76h1Qiq-U7UyXkAlvPDIGOuFFrN5yPx9AbHOrDtUZhs8ghtX',
						'_blank'
					)}>Öppna bildbanken</button
			>
		</section>

		<h1 class="text-6xl text-center font-bold la-luxes-script mb-8">Bra att Veta</h1>

		<section class="mb-32 grid custom:grid-cols-2 gap-10">
			<Card
				title="Mat och dryck"
				content="I samband med brudskål serveras det bubbel och snittar. Till middagen kommer det att dukas upp till buffe och påföljande efterrätt. Vi bjuder på två glas dryck under middagen. Baren kommer vara öppen till självkostnadspris under kvällen."
				imgSrc="matochdryck.jpg"
				alt="Table setup for an event"
				id="mat"
			/>

			<Card
				title="Klädsel"
				content="Ett förslag är kavaj för herrar. Val av färg både på kavajen och skjortan gör du själv. För damer kan ju klänning, kjol, byxdress eller dräkt vara passande.
        Men oavsett är det viktiga att du känner dig bekväm och fin."
				imgSrc="kladsel.jpeg"
				alt="Dress code demonstration"
				id="kladsel"
			/>

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

			<Card
				title="Barn"
				content="Era barn är naturligtvis välkomna på vigseln och under middagen, efter 20:00 har vi planerat att dansgolvet öppnas och då tänker vi att det är dags för barnen att avlägsna sig. Spädbarn är självklart välkomna under hela firandet."
				imgSrc="barn.jpg"
				alt="Children at an event"
				id="barn"
			/>
		</section>

		<h1 id="onskelista" class="text-6xl text-center font-bold la-luxes-script mb-8">Önskelista</h1>
		<section class="mb-32 shadow-xl p-8 custom:p-12 bg-white">
			<p>
				Din närvaro är allt vi önskar. Men vill ni ändå uppmärksamma vår dag med en gåva är ett
				bidrag till vår bröllopsresa en uppskattad gåva, swisha till 070-3229775.
			</p>
		</section>

		<h1 id="tal" class="text-6xl text-center font-bold la-luxes-script mb-8">Tal</h1>
		<section class="mb-32 shadow-xl p-8 custom:p-12 bg-white">
			<div class="space-y-4">
				<p>
					Om du vill hålla tal, uppträda eller spexa får du gärna anmäla det nedan. Vi ser inte
					anmälan utan informationen skickas direkt till vår toastmaster Anne.
				</p>

				<p>För tal brukar ca 5 minuter vara lagom.</p>
				<p>Har du frågor om tal och spex kan du mejla eller ringa våra toastmasters.</p>
				<p>
					<b>Anne Larsen</b><br />
					070-296 69 31 <br /> anne.dragsbaek21@live.dk
				</p>
				<p>
					<b>Daniel Dahlgren</b><br />
					070-206 33 26 <br />
				</p>
			</div>

			{#if formParam === 'tal'}
				<p class="mt-8 text-center text-gray-700">Tack för din anmälan!</p>
			{:else if showTal}
				<form
					class="mt-8 bg-stone-50 grid grid-cols-1 custom:grid-cols-2 gap-4 px-8 pt-6 pb-8 mb-4"
					action="https://submit-form.com/CKkOsyrAP"
				>
					<input type="hidden" name="_redirect" value="{currentLocation}?form=tal" />
					<input type="hidden" name="_append" value="false" />
					{#each speachesForm as { name, label, type, required }}
						<div class="mb-4 flex flex-col justify-between">
							<label class="block text-gray-700 text-sm font-bold mb-2" for={name}>{label}</label>
							<input
								class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
								{type}
								id={name}
								{name}
								{required}
							/>
						</div>
					{/each}
					<div class="col-span-1 custom:col-span-2 flex justify-center">
						<button class="elegant-submit-button" type="submit">Skicka</button>
					</div>
				</form>
			{:else}
				<div class="flex mt-12 justify-center">
					<button class="elegant-submit-button" on:click={() => (showTal = true)}>
						Anmäl tal eller spex</button
					>
				</div>
			{/if}
		</section>

		<h1 id="osa" class="text-6xl text-center font-bold la-luxes-script mb-8">OSA</h1>
		<section class="mb-32 space-y-4 shadow-xl p-8 custom:p-12 bg-white">
			<p>OSA i formuläret nedan senast den 1/7. Har du specialkost? Meddela det här.</p>
			<p>
				Om du har frågor hör gärna av dig till Amanda på
				<a href="tel:073-8482244">073-8482244</a>
				eller <a href="mailto:amanda_fremling@yahoo.se">amanda_fremling@yahoo.se</a>
				.
			</p>

			{#if formParam === 'osa'}
				<p class="mt-8 text-center text-gray-700">Tack för din OSA!</p>
			{:else}
				<p class="text-center text-gray-700">Välj antalet personer att OSA för:</p>

				<div class="flex gap-2 justify-center w-full">
					{#each [1, 2, 3, 4, 5] as number}
						<button
							class={clsx('w-12 h-12 bg-gray-700 text-white', {
								'bg-gray-500': number === numberOfOSA,
								'hover:bg-gray-600': number !== numberOfOSA
							})}
							on:click={() => (numberOfOSA = number)}
						>
							{number}
						</button>
					{/each}
				</div>
			{/if}

			{#if numberOfOSA > 0}
				<form
					class="mt-8 bg-stone-50 grid grid-cols-1 custom:grid-cols-2 gap-4 px-8 pt-6 pb-8 mb-4"
					action="https://submit-form.com/ziknqZsej"
				>
					<input type="hidden" name="_redirect" value="{currentLocation}?form=osa" />
					<input type="hidden" name="_append" value="false" />
					{#each Array(numberOfOSA) as _, number}
						<p class="text-center col-span-1 custom:col-span-2 text-gray-700">
							Person {number + 1}
						</p>
						<input type="hidden" name="osa" value="person-{number + 1}" />
						{#each osaForm as { name, label, type, required }}
							<div class="mb-4 flex flex-col justify-between">
								<label class="block text-gray-700 text-sm font-bold mb-2" for={name + number}
									>{label}</label
								>
								<input
									class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
									{type}
									id={name + number}
									name={name + number}
									{required}
								/>
							</div>
						{/each}
					{/each}
					<div class="col-span-1 custom:col-span-2 flex justify-center">
						<button class="elegant-submit-button" type="submit">Skicka</button>
					</div>
				</form>
			{/if}
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
		@apply text-gray-600;
		font-size: 3rem;
		font-weight: 300;
	}

	.elegant-submit-button {
		@apply bg-gray-700 hover:bg-gray-500;
		color: #ffffff;
		font-weight: 300;
		padding: 12px 48px; /* Larger padding for a bigger button */
		border: none;
		transition: background-color 0.3s ease-in-out;
	}

	.elegant-submit-button:hover {
		cursor: pointer;
	}

	.elegant-submit-button:focus {
		outline: 2px solid #cbd5e0; /* Custom focus ring color */
		outline-offset: 2px;
	}

	@media (max-width: 768px) {
		.countdown span {
			font-size: 2rem;
		}
	}
</style>
