<script>
    export let name;
    export let background = false;
    export let left = false;
    export let right = false;
</script>

<template>
<figure class:background class:left class:right>
    <img alt="{name}" src="./svg/illustrations/{name}.svg">
</figure>
</template>

<style lang="scss">
figure {

    &.background {
        position: absolute;
        z-index: -1;
    }

    &.left {
        width: 80%;
        left: 0;
    }
    &.right {
        width: 80%;
        right: 0;
    }
}

img {
    width: 100%;
    height: auto;
}
</style>