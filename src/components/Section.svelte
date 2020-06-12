<script>
  export let fullscreen = false;
  export let center = false;
  export let horizontal = false;
  export let vertical = false;
  export let dark = false;
</script>

<style lang="scss">
section {
    height: 80vh;
    position: relative;

    &.dark {
        background: #000;
        color: #fff;
    }
    
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

    &.fullscreen {
        height: 100vh;
    }
}
</style>

<section class:center class:horizontal class:vertical class:fullscreen class:dark>
    <slot/>
</section>