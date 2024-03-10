<script lang="ts">
	import Close from './Close.svelte';
	import Hamburger from './Hamburger.svelte';

	const links = [
		{
			name: 'Vigsel',
			href: '#vigsel'
		},
		{
			name: 'Middag och Fest',
			href: '#fest'
		},
		{
			name: 'Bilder',
			href: '#bilder'
		},
		{
			name: 'Mat och dryck',
			href: '#mat'
		},
		{
			name: 'Boende',
			href: '#boende'
		},
		{
			name: 'Klädsel',
			href: '#kladsel'
		},
		{
			name: 'Barn',
			href: '#barn'
		},
		{
			name: 'Önskelista',
			href: '#onskelista'
		},
		{
			name: 'Tal',
			href: '#tal'
		},
		{
			name: 'OSA',
			href: '#osa'
		}
	];

	let showMenu = false;

	const toggleMenu = () => {
		showMenu = !showMenu;

		if (showMenu) {
			document.body.style['overflow-y'] = 'hidden';
		} else {
			document.body.style['overflow-y'] = 'auto';
		}
	};

	// onMount(() => {
	// 	const observer = new IntersectionObserver(
	// 		(entries) => {
	// 			entries.forEach((entry) => {
	// 				const id = entry.target.getAttribute('id');
	// 				const linkIndex = links.findIndex((l) => l.href === `#${id}`);
	// 				console.log('id', id);
	// 				console.log('linkIndex', linkIndex);
	// 				if (linkIndex !== -1) {
	// 					links[linkIndex].isActive = entry.isIntersecting;
	// 				}
	// 			});
	// 		},
	// 		{ threshold: 0.5 }
	// 	); // Adjust the threshold as needed
	//
	// 	document.querySelectorAll('section[id]').forEach((section) => {
	// 		observer.observe(section);
	// 	});
	//
	// 	return () => {
	// 		observer.disconnect();
	// 	};
	// });
</script>

<header
	class={'hidden custom:block sticky top-0 h-[100vh] w-[320px] text-center p-12 space-around bg-stone-200'}
>
	<nav class="h-full">
		<ul class="flex flex-col h-full justify-around">
			{#each links as link}
				<li><a href={link.href} class:active={link.isActive}>{link.name}</a></li>
			{/each}
		</ul>
	</nav>
</header>

<header
	class="custom:hidden relative h-16 w-screen p-4 flex bg-stone-100 justify-between items-center"
>
	<Hamburger on:click={toggleMenu} />

	{#if showMenu}
		<div class="fixed top-0 z-50 left-0 w-screen h-screen bg-stone-50 p-4">
			<Close on:click={toggleMenu} />
			<ul
				class={`space-x-4 h-full flex flex-col justify-evenly items-center libre-baskerville-regular`}
			>
				{#each links as link}
					<li><a href={link.href} on:click={toggleMenu}>{link.name}</a></li>
				{/each}
			</ul>
		</div>
	{/if}
</header>
