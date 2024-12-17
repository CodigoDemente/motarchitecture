<script lang="ts">
	export let isP5enabled: boolean;
	export let src: string;
	export let alt: string;
	export let code: string | null;
</script>

{#if isP5enabled}
	<script>
		import { onMount } from 'svelte';
		import p5 from 'p5';
		let myP5;
		onMount(() => {
			myP5 = new p5((p) => {
				p.setup = () => {
					p.createCanvas(window.innerWidth, window.innerHeight);
				};
				p.draw = () => {
					p.background(0);
					p.fill(255);
					p.ellipse(p.mouseX, p.mouseY, 50, 50);
				};
			});
		});
	</script>
{/if}

<div class="background">
	{#if isP5enabled}
		{code}
	{:else}
		<img {src} {alt} class="animated-image" />
	{/if}
</div>

<style>
	@keyframes invertToNormal {
		0% {
			filter: invert(1);
		}
		100% {
			filter: invert(0);
		}
	}
	.background {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
		z-index: -1;
	}

	.background img {
		width: 50%;
		height: auto;
		border-radius: 8px;
	}

	.animated-image {
		animation: invertToNormal 2s ease-in-out forwards;
	}
</style>
