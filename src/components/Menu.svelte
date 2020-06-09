<script>
    import { fly } from "svelte/transition";
    import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

    const animation = {
        duration: 1000,
        initialDelay: 700,
        delay: 200,
        distance: 200
    }

    const links = [
        {
            url: '#work',
            name: 'work'
        },
        {
            url: '#projects',
            name: 'projects'
        },
        {
            url: '#social',
            name: 'social'
        },
    ]

    function closeMenu() {
        dispatch('closeMenu');
    }
</script>

<nav>
    <ul>
        {#each links as link, i (link)}
            <li
            in:fly="{{
                x: animation.distance,
                duration: animation.duration,
                delay: animation.initialDelay + i * animation.delay
            }}"
            out:fly="{{
                x: animation.distance,
                duration: animation.duration,
                delay: (links.length - 1 - i) * (animation.delay)
            }}"
            >
                <a
                    href="{link.url}"
                    on:click="{closeMenu}"
                >{link.name}</a>
            </li>
        {/each}
    </ul>
</nav>

<style lang="scss">
nav {
    position: fixed;
    width: 80vw;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    right: 0;
    display: flex;
    justify-content: flex-end;
}

ul {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: column;
}

li {
    text-align: right;
}

a {
    color: #000;
    font-size: 48px;
    font-weight: 900;
    position: relative;
    display: block;

    &:hover {
        text-decoration: none;

        &::after {
            height: 40%;
        }
    }

    &::after {
        content: "";
        position: absolute;
        right: 0;
        height: 0%;
        top: 60%;
        width: 120%;
        background: #D9D9D9;
        z-index: -1;
    }
}
</style>