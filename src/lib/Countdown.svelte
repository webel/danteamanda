<script lang="ts">
	import { onMount, onDestroy } from 'svelte';
	import { writable } from 'svelte/store';
	import dayjs from 'dayjs';
	import duration from 'dayjs/plugin/duration.js';
	import utc from 'dayjs/plugin/utc.js';
	import tz from 'dayjs/plugin/timezone.js';
	import customParseFormat from 'dayjs/plugin/customParseFormat.js';

	dayjs.extend(duration);
	dayjs.extend(utc);
	dayjs.extend(tz);
	dayjs.extend(customParseFormat);

	export let from: string;
	export let dateFormat: string = 'YYYY-MM-DD H:m:s';
	export let zone: string | undefined;

	interface RemainingTime {
		days: number;
		hours: number;
		minutes: number;
		seconds: number;
		done: boolean;
	}

	// Convert remaining to a Svelte writable store with the adjusted structure
	let remaining = writable<RemainingTime>({
		days: 0,
		hours: 0,
		minutes: 0,
		seconds: 0,
		done: true
	});

	let timer: ReturnType<typeof setInterval>;

	onMount(() => {
		let target: dayjs.Dayjs;
		try {
			target = zone ? dayjs.tz(from, dateFormat, zone) : dayjs(from, dateFormat);
			console.log('Target Date:', target.toString()); // Debugging: Log the parsed target date
		} catch (e: any) {
			console.warn('[svelte-countdown] Error parsing date:', e.message);
		}

		let now = dayjs();
		console.log('Current Date:', now.toString()); // Debugging: Log the current date

		if (dayjs.isDayjs(target) && target.isValid()) {
			let diff = target.diff(now);

			console.log('Initial Diff (ms):', diff); // Debugging: Log the initial difference

			timer = setInterval(() => {
				now = dayjs(); // Update now at each interval
				diff = target.diff(now); // Recalculate diff

				if (diff > 0) {
					let r = dayjs.duration(diff);
					let totalDays = r.asDays(); // Calculate total days including those from months and years
					remaining.set({
						days: Math.floor(totalDays),
						hours: r.hours(),
						minutes: r.minutes(),
						seconds: r.seconds(),
						done: false
					});
					diff -= 1000;
				} else {
					clearInterval(timer);
					remaining.set({
						days: 0,
						hours: 0,
						minutes: 0,
						seconds: 0,
						done: true
					});
				}
			}, 1000);
		} else {
			console.warn('[svelte-countdown] Invalid target date.');
		}
	});

	onDestroy(() => {
		clearInterval(timer);
	});
</script>

<slot remaining={$remaining} />
