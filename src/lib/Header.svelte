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
</script>

<header
	class={'hidden md:block sticky top-0 h-[100vh] w-[320px] text-center p-12 space-around bg-stone-200'}
>
	<nav class="h-full">
		<ul class="flex flex-col h-full justify-around">
			{#each links as link}
				<li><a href={link.href}>{link.name}</a></li>
			{/each}
		</ul>
	</nav>
</header>

<header class="md:hidden relative h-16 w-screen p-4 flex bg-stone-100 justify-between items-center">
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
