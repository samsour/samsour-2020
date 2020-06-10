<script>
	import { fly } from "svelte/transition";
	import Header from './components/Header.svelte';
	import Intro from './components/Intro.svelte';
	import Cover from './components/Cover.svelte';
	import Menu from './components/Menu.svelte';
	import Footer from './components/Footer.svelte';
	import SocialLinks from './components/SocialLinks.svelte';

	let menuActive = false;

	const animation = {
        duration: 1000,
        delay: 1200,
        distance: 200
    }

	function closeMenu() {
		menuActive = false;
	}
</script>

<Cover bind:menuActive/>
<Header bind:menuActive />
{#if menuActive}
	<Menu on:closeMenu="{closeMenu}" />
{/if}

{#if !menuActive}
	<main
		in:fly="{{
			x: animation.distance,
			duration: animation.duration,
			delay:animation.delay
		}}"
		out:fly="{{
			x: animation.distance,
			duration: animation.duration
		}}"
	>
		<section class="full center">
			<Intro />
		</section>

		<section >
			<h1 id="work">Work</h1>
		</section>

		<section id="social" class="center vertical">
			<SocialLinks />
		</section>
	</main>
{/if}

{#if !menuActive}
	<Footer />
{/if}

<style lang="scss">
	main {
		width: 80vw;
		margin: 0 auto;
		// transition: all 0.25s ease-in-out 0.5s;
		position: relative;
	}

	main.is-hidden {
		transform: translateX(-20%);
		opacity: 0;
		transition: all 0.25s ease-in-out;
	}

	section {
		height: 80vh;
		
		&.center {
			&:not(.vertical):not(.horizontal) {
				display: flex;
				align-items: center;
				justify-content: center;
			}

			&.vertical {
				display: flex;
				align-items: center;
			}

			&.horizontal {
				display: flex;
				justify-content: center;
			}
		}

		&.full {
			height: 100vh;
		}
	}
</style>