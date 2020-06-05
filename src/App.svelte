<script>
	import Header from './components/Header.svelte';
	import Intro from './components/Intro.svelte';
	import Cover from './components/Cover.svelte';
	import Menu from './components/Menu.svelte';

	let menuActive = false;

	function closeMenu() {
		menuActive = false;
	}
</script>

<Cover bind:menuActive/>
<Header bind:menuActive />
{#if menuActive}
	<Menu on:closeMenu="{closeMenu}" />
{/if}

<main class="{ menuActive ? 'is-hidden' : '' }">
	<section class="centered">
		<Intro />
	</section>

	<section >
		<h1 id="work">Work</h1>
	</section>

	<section>
		<h1 id="contact">Contact</h1>
	</section>
</main>

<style lang="scss">
	main {
		width: 80vw;
		max-width: 740px;
		margin: 0 auto;
		transition: all 0.25s ease-in-out 0.5s;
		position: relative;
	}

	main.is-hidden {
		transform: translateX(-20%);
		opacity: 0;
		transition: all 0.25s ease-in-out;
	}

	section {
		height: 100vh;
		
		&.centered {
			display: flex;
			align-items: center;
			justify-content: center;
		}
	}
</style>