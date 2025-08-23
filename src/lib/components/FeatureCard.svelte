<script lang="ts">
	export let icon: string = "⚡️";
	export let title: string;
	export let description: string;
</script>

<div class="feature-card">
	<div class="card-content">
		<div class="feature-icon" role="img" aria-label={title}>
			{icon}
		</div>
		<h3 class="feature-title">{title}</h3>
		<p class="feature-description">{description}</p>
	</div>
</div>

<style>
	.feature-card {
		background: var(--bgn-surface);
		border-radius: var(--border-radius-16);
		height: 100%;
		max-width: 400px;
	}

	.card-content {
		padding: var(--spacing-32);
		height: 100%;
		display: flex;
		flex-direction: column;
	}

	.feature-icon {
		width: var(--dimension-48);
		height: var(--dimension-48);
		border-radius: var(--border-radius-16);
		background-color: var(--bgn-base);
		color: var(--color-inverse);
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: var(--font-size-24);
		margin-bottom: var(--spacing-24);
		box-shadow: var(--shadow-sm);
	}

	.feature-title {
		font-size: var(--font-size-16);
		font-weight: var(--font-weight-semibold);
		color: var(--color-emphasized);
		margin-bottom: var(--spacing-8);
		line-height: var(--line-height-header);
	}

	.feature-description {
		color: var(--color-base);
		line-height: var(--line-height-paragraph);
		font-size: var(--font-size-14);
		flex-grow: 1;
		margin-bottom: 0;
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
	}

	@media (max-width: 480px) {
		.card-content {
			padding: var(--spacing-16);
		}
	}
</style>