<script>
export let menuActive;
</script>

<div class:is-active={menuActive}></div>

<style lang="scss">
div {
    background: #000;
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    width: 200%;
    transform: translateX(100%);
    transition: transform 1s ease-in-out;

    &.is-active {
        transform: translateX(-100%);
    }
}
</style>