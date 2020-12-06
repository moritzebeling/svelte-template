<script>

	import { onMount } from "svelte";
	import Swipe from "swipejs";

	export let images;

	let index = 0;

	let container;
    let swipeGallery;

	onMount(() => {

        swipeGallery = new Swipe(container, {
            draggable: true,
            continuous: false,
            callback: function(i, element) {
				index = i;
            }
        });

    });

</script>

<div class="swipe" bind:this={container}>
	<div class="swipe-wrap">
		{#each images as image, i}

			<figure title="{image.alt}">

				<slot prop={[image, i]}></slot>

				{#if i > 0}
					<button title="Previous image" class="prev" on:click={swipeGallery.prev} />
				{/if}

				{#if i + 1 < images.length}
					<button title="Next image" class="next" on:click={swipeGallery.next} />
				{/if}

			</figure>

		{/each}
	</div>
</div>

<p>{index + 1}/{images.length}</p>

<style lang="scss">

	.swipe {
        overflow: hidden;
        visibility: hidden;
        position: relative;
        height: 100%;
        width: 100%;
    }
    .swipe-wrap {
        overflow: hidden;
        position: relative;
        height: 100%;
    }
	figure {
        position: relative;
        height: 100%;
        width: 100%;
        float: left;
    }

	button {
        position: absolute;
        top: 0;
        width: 50%;
        height: 100%;
        z-index: 5;
        &.prev {
            left: 0;
            cursor: w-resize;
        }
        &.next {
            left: 50%;
            cursor: e-resize;
        }
    }

</style>
