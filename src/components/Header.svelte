<script>
    const name = 'Sam Sauer';
    const menu = 'Menu'

    export let menuActive = false;

    function toggleMenu() {
        menuActive = !menuActive;
    }
</script>

<header>
	<h2>{ name }</h2>
    <div>
        <button on:click="{toggleMenu}">
            <img alt="Menu Button" src="./svg/menu-button.svg">
        </button>
        <span class="rotated">

        </span>
    </div>
</header>

<style>
header {
    width: 80vw;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    margin-top: 120px;
    position: fixed;
    z-index: 500;
    left: 50%;
    transform: translateX(-50%);
}

h2 {
    margin: 0;
    font-size: 24px;
    font-weight: 900;
}

button {
    outline: 0;
    border: 0;
    background: transparent;
    font-size: 24px;
    font-weight: 400;
    cursor: pointer;
}
</style>