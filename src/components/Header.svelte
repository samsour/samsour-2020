<script>
    const name = 'Sam Sauer';
    const menuText = 'menu';
    const closeText = 'close';

    export let menuActive = false;

    function toggleMenu() {
        menuActive = !menuActive;
    }

    function handleLogoClick() {
        menuActive = false;

    }
</script>

<header>
	<div on:click="{handleLogoClick}">{ name }</div>
    <button on:click="{toggleMenu}">
        <img alt="Menu Button" src="./svg/menu-button.svg">
        <span class="rotated">
            {menuActive ? closeText : menuText}
        </span>
    </button>
</header>

<style lang="scss">
header {
    width: 80vw;
    max-width: 1280px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    margin-top: 120px;
    position: fixed;
    z-index: 500;
    left: 50%;
    transform: translateX(-50%);
}

span {
    margin: 0;
    font-size: 24px;
    font-weight: 900;
    cursor: pointer;
}

button {
    outline: 0;
    border: 0;
    background: transparent;
    font-size: 24px;
    font-weight: 400;
    cursor: pointer;
    display: block;
    margin: 0;
    padding: 20px;
    position: relative;
    transform: translate(19px, -20px);

    &:hover {
        .rotated {
            opacity: 1;
        }
    }
}

.rotated {
    color: #D9D9D9;
    display: block;
    transform: rotate(-90deg);
    transform-origin: right;
    z-index: -1;
    position: absolute;
    right: 20%;
    opacity: 0;
}
</style>