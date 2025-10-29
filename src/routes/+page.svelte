<script lang="ts">
	import FeatureCard from '$lib/components/FeatureCard.svelte';
	import AtlButton from '$lib/components/atl-button.svelte';
	import AtlMenu from '$lib/components/AtlMenu.svelte';
	import AtlContainer  from '$lib/components/AtlContainer.svelte';
	import AtlAccordion from '$lib/components/AtlAccordion.svelte';

	const accordionItems = [
		{
			label: 'What is Atlas?',
			content: '<p>Atlas is a modern design system built with Svelte, tailored for the OpenStreetMap community. It provides a comprehensive set of UI components, design tokens, and guidelines to help developers create consistent and user-friendly applications that align with OSM\'s branding and values.</p>'
		},
		{
			label: 'How can I contribute to Atlas?',
			content: 'We welcome contributions from the community! You can contribute by submitting bug reports, feature requests, or even code contributions via our GitHub repository. Please refer to our contributing guidelines for more information on how to get involved.'
		},
		{
			label: 'Is Atlas free to use?',
			content: 'Yes, Atlas is an open-source project released under the MIT License. You are free to use, modify, and distribute it in accordance with the terms of the license.'
		}
	]

	const menuItems = [
		{
			label: 'Action',
			href: '#',
        	icon: null,
        	tiptext: 'Tooltip action example',
        	tipicon: null,
        	badgeNumber: 100,
        	chevron: false,
        	disabled: false,
        	target: '_blank'
		},
		{
			label: 'Action',
			href: '#',
			badgeNumber: 20,
			chevron: true
		},
		{
			label: 'Disabled Action',
			href: '#',
			disabled: true
		}
	];

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
	<AtlAccordion items={accordionItems}></AtlAccordion>
	<AtlContainer variant='close'></AtlContainer>
	<AtlContainer variant='sheet'></AtlContainer>
	<AtlMenu items={menuItems}></AtlMenu>
	<div id="home-main">
		<div id="title">
			<h1 id="main-title">Atlas</h1>
			<h1 id="subtitle">Design System for OpenStreetMap.</h1>
		</div>
		<AtlButton>Start Using</AtlButton>
		<AtlButton variant="outline">GitHub</AtlButton>
	</div>

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

	@import '../style/global.css';

	#home-main {
		margin: var(--spacing-64) 0 0 var(--spacing-64);
	}

	#title {
		margin-bottom: var(--spacing-32);
	}

	#title h1 {
		text-align: start;
		font-weight: 700;
	}

	#subtitle {
		width: var(--dimension-544);
	}

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