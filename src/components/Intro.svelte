<script>
    import { onMount } from 'svelte';
    const speed = 1500; // ms to change words
    const shufflingWords = ['develop', 'design', 'create'];
    let activeIndex = 0;
    
    function shuffleWords() {
        if(activeIndex < shufflingWords.length - 1) {
            activeIndex++;
        } else {
            activeIndex = 0;
        }
    }

    onMount(() => {
		setInterval(() => {
            shuffleWords();
        }, speed)
	});
    
</script>
<template>
    <h1>
        <span>I</span>
        <div class="shuffling-words">
        {#each shufflingWords as word}
            <span class:is-active="{word == shufflingWords[activeIndex]}">{word}</span>
        {/each}
        </div>
        <span>things </span>
        <span>for the web.</span>
    </h1>
</template>
    

<style lang="scss">
h1 {
    font-size: var(--headline-size);
    font-weight: 900;

    @include breakpoint(medium) {
        width: 75%;
    }
}

.shuffling-words {
    display: inline;
    position: relative;
    overflow: hidden;
}

.shuffling-words span:not(.is-active) {
    position: absolute;
    left: 0;
    color: #D9D9D9;
    animation: change-color 1s ease-in-out;
    z-index: -1;
    top: 50%;
    transform: translateY(-50%);
    user-select: none;

    &:nth-child(2) {
        left: 20px;
    }

    &:nth-child(3) {
        left: 20px;
    }
}
</style>