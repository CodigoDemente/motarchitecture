<script lang="ts">
	import type { CardType } from '../../types/Card';

	export let card: CardType;
</script>

<div class="card">
	<div class="card-inner">
		<div class="card-front">
			<img src={card.images[0].src} alt={card.images[0].alt} />
		</div>
		<div class="card-back">
			<img src={card.images[0].src} alt={card.images[0].alt} />
			<div class="card-overlay">
				<h3>{card.title}</h3>
				<p>{card.subtitle}</p>
			</div>
		</div>
	</div>
</div>

<style>
	.card {
		perspective: 1000px;
	}

	.card-inner {
		position: relative;
		transition: transform 0.6s;
		transform-style: preserve-3d;
	}

	.card:hover .card-inner {
		transform: rotateY(180deg);
		cursor: pointer;
	}

	.card-front,
	.card-back {
		position: absolute;
		width: 100%;
		height: 100%;
		backface-visibility: hidden;
	}

	.card-back {
		transform: rotateY(180deg);
	}

	.card-back img {
		filter: invert(1);
	}

	.card-overlay {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}
</style>
