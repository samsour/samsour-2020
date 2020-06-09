<script>
import { fly } from "svelte/transition";

let isActive = false;

const animation = {
    duration: 1000,
    initialDelay: 300,
    delay: 300,
    distance: 200
}

</script>

<footer class:is-active="{isActive}">
    <div class="content">
        <button on:click="{() => isActive = !isActive}" class="open-button">
            {isActive ? 'close' : 'imprint'}
        </button>
        <div class="toggle">
            {#if isActive}
                <ul
                    in:fly="{{x: animation.distance, duration: animation.duration, delay: animation.initialDelay + animation.delay}}"
                    out:fly="{{x: animation.distance, duration: animation.duration, delay: animation.delay * 2 }}"
                >
                    <li>mail <a href="mailto:hi@samsour.de">hi@samsour.de</a></li>
                    <li>phone <a href="tel:+491607512590">+49 160 75 125 90</a></li>
                </ul>

                <ul
                    in:fly="{{x: animation.distance, duration: animation.duration, delay: animation.initialDelay + 2 * animation.delay}}"
                    out:fly="{{x: animation.distance, duration: animation.duration, delay: animation.delay }}"
                >
                    <li>Sam Sauer</li>
                    <li>Nahestr. 22</li>
                    <li>63110 Rodgau</li>
                </ul>

                <ul
                    in:fly="{{x: animation.distance, duration: animation.duration, delay: animation.initialDelay + 3 * animation.delay}}"
                    out:fly="{{x: animation.distance, duration: animation.duration }}"
                >
                    <li>icons made by <a href="https://www.flaticon.com/authors/pixel-perfect" title="Pixel perfect">pixel perfect</a></li>
                </ul>
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
        transition: background-position 500ms ease-out 1s;
        overflow: hidden;


        &.is-active {
            background-position: 0 100%;
            transition: background-position 500ms ease-out;
        }
    }

    button {
        background: transparent;
        border: 0;
        cursor: pointer;
        font-size: 12px;
        font-family: 'Lato', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
        font-weight: 900;
        color: #000;
        user-select: none;
        flex: 1;
        text-align: left;
        transition: color 0ms ease-out 1.2s;

        footer.is-active & {
            transition: color 0ms ease-out 0.2s;
            color: #fff;
        }
    }

    .content {
        width: 80vw;
        margin: 0 auto;
        display: flex;
        justify-content: space-between;
        // font-weight: 900;
        font-size: 12px;
        line-height: 1.75;
    }

    .toggle {
        flex: 3;
        display: flex;
        color: #fff;
        justify-content: space-between;
    }

    ul {
        margin: 0;
        padding: 0;
        list-style: none;
    }

    li {
        display: flex;
        align-items: baseline;
    }

    a {
        color: #fff;
        display: inline-block;
        margin-left: 3px;
        font-weight: 900;
    }
</style>