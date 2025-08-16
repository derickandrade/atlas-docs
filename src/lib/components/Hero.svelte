<script lang="ts">
	export let title: string = "Atlas";
	export let subtitle: string = "Design System for OpenStreetMap";
	export let ctaText: string = "Get Started";
	export let ctaHref: string = "#get-started";
</script>

<section class="hero">
	<div class="container">
		<div class="hero-content">
			<h1 class="hero-title">
				<span class="title-line">{title}</span>
				<span class="subtitle-line">{subtitle}</span>
			</h1>
			<div class="hero-actions">
				<a href={ctaHref} class="cta-button">
					<span>{ctaText}</span>
					<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
						<path d="m9 18 6-6-6-6"/>
					</svg>
				</a>
			</div>
		</div>
	</div>
</section>

<style>
	@import '../../style/global.css';
	.hero {
		background: var(--bgn-base);
		position: relative;
		overflow: hidden;
		min-height: 50vh;
		display: flex;
		align-items: center;
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
		max-width: var(--size-872, 872px);
	}

	.hero-title {
		font-size: var(--font-size-96, 6rem);
		font-weight: var(--font-weight-bold, 700);
		color: var(--color-base);
		margin-bottom: var(--spacing-64, 4rem);
		line-height: var(--line-height-header, 1.1);
		display: flex;
		flex-direction: column;
		gap: 0;
		font-size: 48px;
		font-weight: 600;
		text-align: left;
		max-width: 576px;
	}

	.title-line {
		display: block;
		animation: fadeInUp 0.8s ease forwards;
		line-height: 56px;
		font-size: 48px;
		font-weight: 600;
		max-width: 576px;
	}

	.subtitle-line {
		display: block;
		font-weight: 600;
	}


	.cta-button {
		display: inline-flex;
		align-items: center;
		gap: var(--spacing-8, 0.5rem);
		background: var(--bgn-accent, #6b9b37);
		color: var(--color-inverse, #ffffff);
		padding: var(--spacing-12, 0.75rem) var(--spacing-24, 1.5rem);
		border-radius: var(--border-radius-8, 8px);
		text-decoration: none;
		font-weight: var(--font-weight-semibold, 600);
		font-size: var(--font-size-16, 1rem);
		font-family: var(--font-family-sans-serif, system-ui);
		transition: all 0.3s ease;
		box-shadow: var(--shadow-md, 0 4px 6px -1px rgba(0, 0, 0, 0.1));
		position: relative;
		overflow: hidden;
	}

	.cta-button::before {
		content: '';
		position: absolute;
		top: 0;
		left: -100%;
		width: 100%;
		height: 100%;
		background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
		transition: left 0.5s ease;
	}

	.cta-button:hover::before {
		left: 100%;
	}

	.cta-button:hover {
		background: var(--bgn-accent-hover, #5a8230);
		transform: translateY(-2px);
		box-shadow: var(--shadow-lg, 0 10px 15px -3px rgba(0, 0, 0, 0.1));
	}

	.cta-button:active {
		background: var(--bgn-accent-active, #4f7029);
		transform: translateY(0);
		box-shadow: var(--shadow-sm, 0 1px 2px 0 rgba(0, 0, 0, 0.05));
	}

	.cta-button svg {
		transition: transform 0.2s ease;
	}

	.cta-button:hover svg {
		transform: translateX(2px);
	}

	/* Animations */
	@keyframes fadeInUp {
		from {
			opacity: 0;
			transform: translateY(30px);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}

	/* Responsive Design */
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

		.cta-button {
			padding: var(--spacing-12, 0.75rem) var(--spacing-24, 1.5rem);
		}
	}

	@media (max-width: 480px) {
		.hero-title {
			font-size: var(--font-size-48, 3rem);
		}
	}
</style>