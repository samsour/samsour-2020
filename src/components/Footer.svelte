<script>
let isActive = false;
</script>

<footer class:is-active="{isActive}">
    <div class="content">
        <button on:click="{() => isActive = !isActive}" class="open-button">
            {isActive ? 'close' : 'imprint'}
        </button>
        <div class="overlay">
            {#if isActive}
                <ul>
                    <li>mail <a href="mailto:hi@samsour.de">hi@samsour.de</a></li>
                    <li>phone <a href="tel:+491607512590">+49 160 75 125 90</a></li>
                </ul>

                <ul>
                    <li>Sam Sauer</li>
                    <li>Nahestr. 22</li>
                    <li>63110 Rodgau</li>
                </ul>

                <span>icons made by </span><a href="https://www.flaticon.com/authors/pixel-perfect" title="Pixel perfect">pixel perfect</a>
            {/if}
        </div>
    </div>
</footer>

<style lang="scss">
    footer {
        height: 25vh;
        display: flex;
        align-items: center;
        position: relative;
        background: linear-gradient(to bottom, #fff 50%, #000 50%) no-repeat;
        background-size: 100% 200%;
        background-position: 0 0;
        transition: background-position 250ms ease-out;

        &.is-active {
            background-position: 0 100%;
        }
    }

    button {
        background: transparent;
        border: 0;
        cursor: pointer;
        font-size: 13px;
        font-family: 'Lato', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
        font-weight: 900;
        color: #000;
        user-select: none;

        footer.is-active & {
            color: #fff;
        }
    }

    .content {
        width: 80vw;
        margin: 0 auto;
        display: flex;
        justify-content: space-between;
    }

    .overlay {
        display: flex;
        color: #fff;
    }

    ul {
        margin: 0;
        padding: 0;
        list-style: none;
    }

    a {
        color: #fff;
        display: block;
    }
</style>