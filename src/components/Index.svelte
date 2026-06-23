<script>
	let loaded = true;
</script>

<svelte:head>
	<title>Datazoba</title>
	<meta name="viewport" content="width=device-width, initial-scale=1" />
</svelte:head>

<main class:loaded={loaded}>
	<div class="background" aria-hidden="true"></div>
	<div class="container">
		<p class="eyebrow">An African digital publishing studio.</p>
		<h1>
			<span class="word">We</span>
			<span class="word">are</span>
			<span class="word">building</span>
			<span class="word highlight">datazoba</span>
		</h1>
	</div>
</main>

<style>
	:global(body) {
		margin: 0;
		padding: 0;
		background: transparent;
		color: inherit;
		font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
		overflow: hidden;
	}

	main {
		position: relative;
		min-height: 100vh;
		display: grid;
		place-items: center;
		padding: 2rem;
		overflow: hidden;
		background: transparent;
		opacity: 0;
		transition: opacity 0.8s ease-out;
	}

	main.loaded {
		opacity: 1;
	}

	.background {
		display: none;
	}

	.container {
		position: relative;
		z-index: 1;
		max-width: 960px;
		text-align: center;
	}

	.eyebrow {
		margin: 0 0 1.2rem;
		font-size: 0.95rem;
		font-weight: 700;
		letter-spacing: 0.35em;
		text-transform: uppercase;
		color: inherit;
		opacity: 0;
		transform: translateY(1rem);
		transition: transform 0.9s cubic-bezier(0.16, 1, 0.3, 1), opacity 0.9s ease;
	}

	main.loaded .eyebrow {
		transform: translateY(0);
		opacity: 1;
	}

	h1 {
		margin: 0;
		font-size: clamp(3rem, 10vw, 7rem);
		line-height: 0.95;
		font-weight: 700;
		letter-spacing: -0.035em;
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		gap: 0.16em;
		text-wrap: balance;
	}

	.word {
		display: inline-block;
		opacity: 0;
		transform: translateY(1.8rem) scale(0.96);
		filter: blur(6px);
		transition:
			opacity 0.95s cubic-bezier(0.16, 1, 0.3, 1),
			transform 0.95s cubic-bezier(0.16, 1, 0.3, 1),
			filter 0.95s ease;
	}

	main.loaded .word {
		opacity: 1;
		transform: translateY(0) scale(1);
		filter: blur(0);
	}

	.word:nth-child(2) {
		transition-delay: 0.14s;
	}

	.word:nth-child(3) {
		transition-delay: 0.28s;
	}

	.word:nth-child(4) {
		transition-delay: 0.42s;
	}

	.highlight {
		color: inherit;
		font-weight: 800;
		transform-origin: center bottom;
		animation: pulseText 2.8s ease-in-out infinite;
	}

	@keyframes pulseText {
		0%,
		100% {
			transform: scale(1);
		}
		50% {
			transform: scale(1.03);
		}
	}

	@keyframes shimmer {
		to {
			background-position: 200% center;
		}
	}

	@keyframes drift {
		from {
			transform: translate3d(-2%, -1%, 0) scale(1);
		}
		to {
			transform: translate3d(2%, 1%, 0) scale(1.04);
		}
	}

	@media (prefers-reduced-motion: reduce) {
		main {
			opacity: 1;
			transition: none;
		}

		.background,
		.highlight {
			animation: none;
		}

		.word {
			opacity: 1;
			transform: none;
			filter: none;
			transition: none;
		}
	}
</style>
