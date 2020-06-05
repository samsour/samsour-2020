<script>
	import Header from './components/Header.svelte';
	import Intro from './components/Intro.svelte';
	import Cover from './components/Cover.svelte';
	import Menu from './components/Menu.svelte';

	const intro = 'I develop things for the web.'
	let menuActive = false;
</script>


<Cover bind:menuActive/>
<Header bind:menuActive />
{#if menuActive}
	<Menu />
{/if}

<main class="{ menuActive ? 'is-hidden' : '' }">
	<section>
		<Intro />
	</section>

	<section>
		<h1>{ intro }</h1>
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
		display: flex;
		align-items: center;
		justify-content: center;
	}
</style>