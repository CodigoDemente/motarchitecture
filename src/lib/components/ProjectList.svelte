<script lang="ts">
	import Card from './Card.svelte';
	import type { ProjectCard } from '../../types/Card';

	export let list: ProjectCard[];
	const colPos = [1, 5, 2, 5, 1, 6, 3];
	const rowPos = [1, 3, 5, 8, 10, 11, 12, 14, 15];
	const sizeToSpan = {
		small: 1,
		medium: 2,
		large: 3
	};
</script>

<ul class="z-1 relative grid h-screen grid-flow-row grid-cols-6">
	{#each list as card, i}
		<li class={`col-span-${sizeToSpan[card.size]} col-start-${colPos[i]} row-start-${rowPos[i]}`}>
			<Card {card} />
		</li>
	{/each}
</ul>
