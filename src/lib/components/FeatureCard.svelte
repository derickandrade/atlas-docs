<script lang="ts">
	export let icon: string = "⚡️";
	export let title: string;
	export let description: string;
	export let href: string | null = null;
	export let delay: number = 0;
</script>

<div class="feature-card" style="animation-delay: {delay}s;">
	{#if href}
		<a {href} class="card-link">
			<div class="card-content">
				<div class="feature-icon" role="img" aria-label={title}>
					{icon}
				</div>
				<h3 class="feature-title">{title}</h3>
				<p class="feature-description">{description}</p>
				<div class="card-arrow">
					<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
						<path d="m9 18 6-6-6-6"/>
					</svg>
				</div>
			</div>
		</a>
	{:else}
		<div class="card-content">
			<div class="feature-icon" role="img" aria-label={title}>
				{icon}
			</div>
			<h3 class="feature-title">{title}</h3>
			<p class="feature-description">{description}</p>
		</div>
	{/if}
</div>

<style>
	.feature-card {
		background: var(--bgn-surface);
		border: var(--border-style-base);
		border-radius: var(--border-radius-16);
		transition: all 0.3s ease;
		position: relative;
		overflow: hidden;
		animation: fadeInUp 0.6s ease forwards;
		opacity: 0;
		height: 100%;
	}

	.feature-card::before {
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		height: 3px;
		background: linear-gradient(90deg, var(--color-accent), var(--color-accent-hover));
		transform: scaleX(0);
		transition: transform 0.3s ease;
		transform-origin: left;
	}

	.feature-card:hover::before {
		transform: scaleX(1);
	}

	.feature-card:hover {
		transform: translateY(-4px);
		box-shadow: var(--shadow-xl);
		border-color: var(--border-color-accent);
	}

	.card-link {
		text-decoration: none;
		color: inherit;
		display: block;
		height: 100%;
	}

	.card-content {
		padding: var(--spacing-32);
		height: 100%;
		display: flex;
		flex-direction: column;
		position: relative;
	}

	.feature-icon {
		width: var(--dimension-48);
		height: var(--dimension-48);
		border-radius: var(--border-radius-16);
		background: linear-gradient(135deg, var(--color-accent), var(--color-accent-hover));
		color: var(--color-inverse);
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: var(--font-size-24);
		margin-bottom: var(--spacing-24);
		transition: all 0.3s ease;
		box-shadow: var(--shadow-sm);
	}

	.feature-card:hover .feature-icon {
		transform: scale(1.05);
		box-shadow: var(--shadow-md);
	}

	.feature-title {
		font-size: var(--font-size-24);
		font-weight: var(--font-weight-semibold);
		color: var(--color-emphasized);
		margin-bottom: var(--spacing-16);
		line-height: var(--line-height-header);
	}

	.feature-description {
		color: var(--color-base);
		line-height: var(--line-height-paragraph);
		font-size: var(--font-size-16);
		flex-grow: 1;
		margin-bottom: 0;
	}

	.card-arrow {
		position: absolute;
		top: var(--spacing-24);
		right: var(--spacing-24);
		width: var(--dimension-32);
		height: var(--dimension-32);
		border-radius: var(--border-radius-8);
		background: var(--bgn-base);
		display: flex;
		align-items: center;
		justify-content: center;
		opacity: 0;
		transform: translateX(-8px);
		transition: all 0.3s ease;
		color: var(--color-accent);
	}

	.card-link:hover .card-arrow {
		opacity: 1;
		transform: translateX(0);
	}

	/* Alternative icon styles for different types */
	.feature-card:nth-child(1) .feature-icon {
		background: linear-gradient(135deg, var(--blue-500), var(--blue-400));
	}

	.feature-card:nth-child(2) .feature-icon {
		background: linear-gradient(135deg, var(--green-500), var(--green-400));
	}

	.feature-card:nth-child(3) .feature-icon {
		background: linear-gradient(135deg, var(--purple-500), var(--purple-400));
	}

	.feature-card:nth-child(4) .feature-icon {
		background: linear-gradient(135deg, var(--orange-500), var(--orange-400));
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

	/* Focus states for accessibility */
	.card-link:focus {
		outline: none;
	}

	.card-link:focus .feature-card {
		border: var(--border-style-focus);
		transform: translateY(-2px);
		box-shadow: var(--shadow-lg);
	}

	/* Responsive Design */
	@media (max-width: 768px) {
		.card-content {
			padding: var(--spacing-24);
		}

		.feature-icon {
			width: var(--dimension-40);
			height: var(--dimension-40);
			font-size: var(--font-size-20);
			margin-bottom: var(--spacing-16);
		}

		.feature-title {
			font-size: var(--font-size-20);
			margin-bottom: var(--spacing-12);
		}

		.feature-description {
			font-size: var(--font-size-16);
		}

		.card-arrow {
			top: var(--spacing-16);
			right: var(--spacing-16);
			width: var(--dimension-24);
			height: var(--dimension-24);
		}
	}

	@media (max-width: 480px) {
		.card-content {
			padding: var(--spacing-16);
		}
	}
</style>