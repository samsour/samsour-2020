<script>
	const name = 'Sam Sauer';
	let activeSidebar = false;
	const intro = 'I develop things for the web.'
</script>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Lato:wght@900&display=swap');

	:global(body) {
		background: #fff;
		color: #000;
		padding: 0;
		margin: 0;
		font-family: 'Lato', sans-serif;
	}

	header, main {
		width: 80vw;
		margin: 0 auto;
	}

	h1 {
		margin: 0;
		font-size: 100px;
		width: 70%;
		margin: auto;
	}

	header {
		display: flex;
		justify-content: space-between;
		margin-top: 120px;
		position: fixed;
		left: 50%;
		transform: translateX(-50%);
	}

	main {
		transition: transform 0.25s ease-in-out;
		position: relative;
	}

	main.is-transformed {
		transform: translateX(-10%);
	}

	section {
		height: 100vh;
		display: flex;
		align-items: center;
		justify-content: center;
	}
</style>

<header>
	<span>{ name }</span>
	<button on:click="{() => activeSidebar = !activeSidebar }">Menu</button>
</header>

<main class="{ activeSidebar ? 'is-transformed' : '' }">
	<section>
		<h1>{ intro }</h1>
	</section>
	<section>
		<h1>{ intro }</h1>
	</section>
</main>