<script lang="ts">
	import Hero from '$lib/components/Hero.svelte';
	import FeatureCard from '$lib/components/FeatureCard.svelte';

	// Dados das features
	const features = [
		{
			icon: "⚡️",
			title: "Svelte-Powered",
			description: "Components optimized with Svelte for efficient rendering and zero runtime overhead.",
		},
		{
			icon: "✨",
			title: "Flexible Theming",
			description: "Native support for light/dark themes and customizations using design tokens.",
		},
		{
			icon: "🤝",
			title: "Community-Driven",
			description: "Built collaboratively with the OSM community, open to contributions and adaptable to diverse mapping needs.",
		}
	];
</script>

<svelte:head>
	<title>Atlas</title>
	<meta name="description" content="A modern design system built with Svelte for the OpenStreetMap community" />
</svelte:head>

<main>
	<!-- Hero Section -->
	<Hero 
		title="Atlas"
		subtitle="Design System for OpenStreetMap."
	/>

	<!-- Features Section -->
	<section class="features">
		<div class="container">

			<div class="features-grid">
				{#each features as feature}
					<FeatureCard 
						icon={feature.icon}
						title={feature.title}
						description={feature.description}
					/>
				{/each}
			</div>
		</div>
	</section>

	<!-- Inspiration Section -->
	<section class="inspiration">
		<div class="container">
			<div class="inspiration-content">
				<p class="inspiration-description">
					This project was inspired by 
					<a href="https://doc.wikimedia.org/codex/latest/" class="inspiration-link" target="_blank" rel="noopener noreferrer">
						Wikimedia's Codex
					</a>, 
					an open-source design system developed by the Wikimedia Foundation. Many of the 
					guidelines and Design Tokens in this Design System were adapted or reused from Codex.
				</p>
				
			</div>
		</div>
	</section>
</main>

<style>
	.container {
		max-width: 80rem;
		margin: 0 auto;
		padding: 0 var(--spacing-32);
	}

	/* Features Section */
	.features {
		background: var(--bgn-base);
	}

	.features-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
		margin-top: var(--spacing-64);
	}

	/* Inspiration Section */
	.inspiration {
		padding-top: 40px;
		background: var(--bgn-base);
	}

	.inspiration-content {
		max-width: 78rem;
		margin: 0 auto;
		text-align: justify;
		padding-right: var(--dimension-32);
	}

	.inspiration-description {
		font-size: var(--font-size-14);
		color: var(--color-base);
		line-height: var(--line-height-paragraph);
		max-width: none;
	}

	.inspiration-link {
		color: var(--color-link);
		text-decoration: var(--text-decoration-underline);
		font-weight: var(--font-weight-semibold);
		transition: color 0.2s ease;
	}

	.inspiration-link:hover {
		color: var(--color-link-hover);
	}

	.inspiration-link:visited {
		color: var(--color-link-visited);
	}

	/* Responsive Design */
	@media (max-width: 1200px) {
		.features-grid {
			grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
			gap: var(--spacing-24);
		}
	}

	@media (max-width: 768px) {
		.container {
			padding: 0 var(--spacing-16);
		}

		.features {
			padding: var(--spacing-64) 0;
		}

		.inspiration {
			padding: var(--spacing-64) 0;
		}

		.inspiration-description {
			font-size: var(--font-size-16);
		}

		.features-grid {
			grid-template-columns: 1fr;
			gap: var(--spacing-16);
			margin-top: var(--spacing-40);
		}
	}

	@media (max-width: 480px) {
		.container {
			padding: 0 var(--spacing-12);
		}

		.features-title {
			font-size: var(--font-size-24);
		}

		.inspiration-title {
			font-size: var(--font-size-24);
		}
	}
</style>