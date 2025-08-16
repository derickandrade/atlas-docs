<script lang="ts">
	import { page } from '$app/state';
	import { onMount } from 'svelte';
	import github from '$lib/images/github.svg';

	let isDarkMode = false;

	onMount(() => {
		// Verifica a preferência salva ou do sistema
		const savedTheme = localStorage.getItem('theme');
		const systemPrefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
		
		isDarkMode = savedTheme === 'dark' || (!savedTheme && systemPrefersDark);
		updateTheme();
	});

	function toggleTheme() {
		isDarkMode = !isDarkMode;
		updateTheme();
		localStorage.setItem('theme', isDarkMode ? 'dark' : 'light');
	}

	function updateTheme() {
		if (isDarkMode) {
			document.documentElement.style.colorScheme = 'dark';
		} else {
			document.documentElement.style.colorScheme = 'light';
		}
	}
</script>

<header>
	<div class="container">
		<div class="header-content">
			<!-- Logo Section -->
			<div class="logo-section">
				<a href="/" class="logo">
					Atlas
				</a>
			</div>

			<!-- Search Button -->
			<div class="search-section">
				<button class="search-button" type="button" aria-label="Search">
					<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
						<circle cx="11" cy="11" r="8"/>
						<path d="m21 21-4.35-4.35"/>
					</svg>
					<span>Pesquisar</span>
					<kbd class="search-kbd">⌘K</kbd>
				</button>
			</div>

			<!-- Navigation Menu -->
			<nav class="nav-menu">
				<a 
					href="/using" 
					class="nav-item" 
					class:active={page.url.pathname === '/using'}
				>
					Using Atlas
				</a>
				<a 
					href="/contributing" 
					class="nav-item"
					class:active={page.url.pathname === '/contributing'}
				>
					Contributing
				</a>
				<a 
					href="/style-guide" 
					class="nav-item"
					class:active={page.url.pathname === '/style-guide'}
				>
					Style Guide
				</a>
				<a 
					href="/design-tokens" 
					class="nav-item"
					class:active={page.url.pathname === '/design-tokens'}
				>
					Design Tokens
				</a>
				<a 
					href="/components" 
					class="nav-item"
					class:active={page.url.pathname === '/components'}
				>
					Components
				</a>
			</nav>

			<!-- Theme Toggle and GitHub -->
			<div class="actions-section">
				<!-- Theme Toggle Switch -->
				<button 
					class="theme-toggle" 
					on:click={toggleTheme}
					aria-label={isDarkMode ? 'Mudar para tema claro' : 'Mudar para tema escuro'}
				>
					<div class="toggle-track" class:dark={isDarkMode}>
						<div class="toggle-thumb" class:dark={isDarkMode}>
							{#if isDarkMode}
								<!-- Moon Icon -->
								<svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
									<path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/>
								</svg>
							{:else}
								<!-- Sun Icon -->
								<svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
									<circle cx="12" cy="12" r="5"/>
									<path d="M12 1v2M12 21v2M4.22 4.22l1.42 1.42M18.36 18.36l1.42 1.42M1 12h2M21 12h2M4.22 19.78l1.42-1.42M18.36 5.64l1.42-1.42"/>
								</svg>
							{/if}
						</div>
					</div>
				</button>

				<!-- GitHub Link -->
				<a 
					href="https://github.com/Gustavo22Soaresh/Design-Atlas" 
					class="github-link"
					aria-label="GitHub Repository"
					target="_blank"
					rel="noopener noreferrer"
				>
					<img src={github} alt="GitHub" />
				</a>
			</div>
		</div>
	</div>
</header>

<style>
	@import '../style/global.css';
	header {
		position: sticky;
		top: 0;
		z-index: 100;
		width: 100%;
		background: var(--bgn-base);
		border-bottom: var(--border-style-base);
		backdrop-filter: blur(10px);
		-webkit-backdrop-filter: blur(10px);
	}

	.container {
		max-width: var(--dimension-1440);
		margin: 0 auto;
		padding: 0 var(--spacing-32);
	}

	.header-content {
		display: flex;
		justify-content: space-between;
		align-items: center;
		height: var(--dimension-64);
		gap: var(--spacing-24);
	}

	/* Logo Section */
	.logo-section {
		flex-shrink: 0;
	}

	.logo {
		display: flex;
		align-items: center;
		text-decoration: none;
		color: var(--color-emphasized);
		font-weight: var(--font-weight-bold);
		font-size: var(--font-size-20);
		transition: opacity 0.2s ease;
	}

	.logo:hover {
		opacity: 0.8;
	}

	/* Search Section */
	.search-section {
		flex: 1;
		max-width: var(--size-416);
		margin-left: var(--spacing-40);
	}

	.search-button {
		display: flex;
		align-items: center;
		justify-content: space-between;
		width: 100%;
		padding: var(--spacing-8) var(--spacing-12);
		border: var(--border-style-base);
		border-radius: var(--border-radius-8);
		background: var(--bgn-base);
		color: var(--color-subtle);
		font-size: var(--font-size-16);
		font-family: var(--font-family-sans-serif);
		cursor: pointer;
		transition: all 0.2s ease;
	}

	.search-button:hover {
		border-color: var(--border-color-accent);
		background: var(--bgn-surface);
	}

	.search-button:focus {
		outline: none;
		border: var(--border-style-focus);
	}

	.search-button svg {
		margin-right: var(--spacing-8);
		color: var(--color-subtle);
	}

	.search-kbd {
		background: var(--bgn-surface);
		border: var(--border-style-base);
		border-radius: var(--border-radius-4);
		padding: 2px var(--spacing-8);
		font-size: var(--font-size-12);
		color: var(--color-subtle);
		font-family: var(--font-family-sans-serif);
		font-weight: var(--font-weight-semibold);
	}

	/* Navigation Menu */
	.nav-menu {
		display: flex;
		align-items: center;
		gap: var(--spacing-32);
		margin-left: auto;
		margin-right: var(--spacing-24);
	}

	.nav-item {
		color: var(--color-base);
		text-decoration: none;
		font-weight: var(--font-weight-semibold);
		font-size: var(--font-size-16);
		padding: var(--spacing-8) 0;
		border-bottom: 2px solid transparent;
		transition: all 0.2s ease;
		white-space: nowrap;
	}

	.nav-item:hover {
		color: var(--color-accent);
	}

	.nav-item.active {
		color: var(--color-accent);
		border-bottom-color: var(--color-accent);
	}

	/* Actions Section */
	.actions-section {
		display: flex;
		align-items: center;
		gap: var(--spacing-16);
		flex-shrink: 0;
	}

	/* Theme Toggle */
	.theme-toggle {
		background: none;
		border: none;
		cursor: pointer;
		padding: var(--spacing-4);
	}

	.toggle-track {
		width: 48px;
		height: 24px;
		background: var(--bgn-base);
		border: var(--border-style-base);
		border-radius: var(--border-radius-24);
		position: relative;
		transition: all 0.2s ease;
	}

	.toggle-track.dark {
		background: var(--color-accent);
		border-color: var(--color-accent);
	}

	.toggle-thumb {
		width: 20px;
		height: 20px;
		background: var(--bgn-surface);
		border-radius: 50%;
		position: absolute;
		top: 1px;
		left: 1px;
		display: flex;
		align-items: center;
		justify-content: center;
		transition: all 0.2s ease;
		box-shadow: var(--shadow-sm);
		color: var(--color-base);
	}

	.toggle-thumb.dark {
		transform: translateX(24px);
		background: var(--bgn-surface);
		color: var(--color-emphasized);
	}

	.theme-toggle:hover .toggle-track {
		background: var(--bgn-surface-hover);
	}

	.theme-toggle:hover .toggle-track.dark {
		background: var(--color-accent-hover);
	}

	/* GitHub Link */
	.github-link {
		display: flex;
		align-items: center;
		justify-content: center;
		width: var(--dimension-40);
		height: var(--dimension-40);
		border-radius: var(--border-radius-8);
		transition: background-color 0.2s ease;
	}

	.github-link:hover {
		background-color: var(--bgn-surface-hover);
	}

	.github-link img {
		width: var(--dimension-20);
		height: var(--dimension-20);
		object-fit: contain;
		filter: brightness(0) saturate(100%) invert(0.3) sepia(0) saturate(0) hue-rotate(0deg) brightness(0.7) contrast(1.2);
	}

	/* Dark mode GitHub icon filter */
	:global([color-scheme="dark"]) .github-link img {
		filter: brightness(0) saturate(100%) invert(0.8) sepia(0) saturate(0) hue-rotate(0deg) brightness(1.2) contrast(1);
	}

	/* Responsive Design */
	@media (max-width: 1200px) {
		.nav-menu {
			gap: var(--spacing-24);
		}

		.nav-item {
			font-size: calc(var(--font-size-16) - 1px);
		}
	}

	@media (max-width: 768px) {
		.container {
			padding: 0 var(--spacing-16);
		}

		.search-section {
			display: none;
		}

		.nav-menu {
			display: none;
		}

		.header-content {
			justify-content: space-between;
		}

		.logo {
			font-size: var(--font-size-20);
		}
	}

	@media (max-width: 480px) {
		.container {
			padding: 0 var(--spacing-12);
		}

		.header-content {
			height: calc(var(--dimension-64) - 8px);
		}

		.actions-section {
			gap: var(--spacing-12);
		}
	}
</style>