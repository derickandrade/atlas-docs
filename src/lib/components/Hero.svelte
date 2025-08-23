<script lang="ts">
	import AtlButton  from '$lib/components/atl-button.svelte';
	
	export let title: string = "Atlas";
	export let subtitle: string = "Design System for OpenStreetMap.";
</script>

<section class="hero">
	<div class="container">
		<div class="hero-content">
			<h1 class="hero-title">
				<span class="title-line">{title}</span>
				<span class="subtitle-line">{subtitle}</span>
			</h1>
			<span id="home-buttons">
				<AtlButton><a class="button-link" target="_blank" rel="noopener noreferrer" href="/about">Start Using</a></AtlButton>
				<AtlButton variant="outline" ><a href="https://github.com/OSMBrasil/design-atlas" class="button-link" aria-label="GitHub Link" target="_blank" rel="noopener noreferrer">GitHub</a></AtlButton>
			</span>
		</div>
	</div>
</section>

<style>
	@import '../../style/global.css';
	.hero {
		background: var(--bgn-base);
		position: relative;
		overflow: hidden;
		display: flex;
	}

	.container {
		max-width: var(--dimension-1440, 1440px);
		margin: 0 auto;
		padding: 0 var(--spacing-32, 2rem);
		position: relative;
		z-index: 1;
		width: 100%;
	}

	.hero-content {
		text-align: left;
		padding-top: var(--dimension-64);
		max-width: var(--size-872, 872px);
	}

	.hero-title {
		font-size: var(--font-size-60) !important;
		font-weight: var(--font-weight-bold, 700);
		color: var(--color-base);
		margin-bottom: var(--spacing-64, 4rem);
		margin: 0 auto;
		line-height: var(--line-height-header, 1.1);
		display: flex;
		flex-direction: column;
		gap: 0;
		font-size: 48px;
		font-weight: 600;
		line-height: 64px;
		text-align: left;
		max-width: 576px;
	}

	.title-line {
		display: block;
		font-weight: 600;
		max-width: 576px;
	}

	.subtitle-line {
		display: block;
		font-weight: 600;
		margin-bottom: var(--dimension-24);
	}

	span#home-buttons {
		margin-left: calc(var(--dimension-160) - 10px);
	}

	.button-link {
		text-decoration: none;
		color: inherit;
	}

	@media (max-width: 768px) {
		.hero {
			padding: var(--spacing-64, 4rem) 0;
			min-height: 50vh;
		}

		.container {
			padding: 0 var(--spacing-16, 1rem);
		}

		.hero-content {
			text-align: center;
		}

		.hero-title {
			font-size: var(--font-size-60, 3.75rem);
			margin-bottom: var(--spacing-40, 2.5rem);
		}
	}

	@media (max-width: 480px) {
		.hero-title {
			font-size: var(--font-size-48, 3rem);
		}
	}
</style>