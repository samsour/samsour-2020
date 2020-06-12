<script>
	import { fly } from "svelte/transition";
	import Header from './components/Header.svelte';
	import Section from './components/Section.svelte';
	import Illustration from './components/Illustration.svelte';
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

<template>
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
			<Section fullscreen center vertical>
				<Illustration background left name="sitting" />
				<Intro />
			</Section>

			<Section center dark>
				<h1>Work</h1>
			</Section>

			<Section center vertical>
				<SocialLinks />
			</Section>
		</main>
	{/if}

	{#if !menuActive}
		<Footer />
	{/if}
</template>

<style lang="scss">

main {
	width: var(--content-width);
	max-width: var(--max-width);
	margin: 0 auto;
	position: relative;
}

main.is-hidden {
	transform: translateX(-20%);
	opacity: 0;
	transition: all 0.25s ease-in-out;
}
</style>