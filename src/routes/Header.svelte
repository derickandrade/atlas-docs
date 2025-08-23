<script lang="ts">
	import { page } from '$app/state';
	import { onMount } from 'svelte';
	import github from '$lib/images/github.svg';

	let isDarkMode = false;

	$: currentPath = page.url?.pathname;

	onMount(() => {
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
	<nav>
		<span class="container">
			<a class="title" href="/" aria-current={currentPath === '/' ? 'page' : undefined}>
				Atlas
			</a>
			<button>
				Pesquisar
			</button>
		</span>

		<span class="nav-links">
			<a href="/">
				Using Atlas
			</a>
			<a href="/">
				Contributing
			</a>
			<a href="/">
				Style Guide
			</a>
			<a href="/">
				Design Tokens
			</a>
			<a class="div-line" href="/components/overview" aria-current={page.url.pathname.startsWith('/components') ? 'page' : undefined}>
				Components
			</a>
		</span>

		<span class="theme-button">
			<button
				class="theme-toggle"
				on:click={toggleTheme}
				aria-label={isDarkMode ? 'Switch to light theme' : 'Switch to dark theme'}
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
		</span>

		<!-- GitHub Link -->
		<a
			href="https://github.com/Gustavo22Soaresh/Design-Atlas"
			class="github-link"
			aria-label="GitHub Repository"
			target="_blank"
			rel="noopener noreferrer"
		>
			<img width="20" src={github} alt="GitHub" />
		</a>

	</nav>
</header>

<style>
	@import '../style/global.css';

	header {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		z-index: 30;
		background-color: var(--bgn-base);
		
	}

	nav {
		position: relative;
		margin: var(--dimension-16) auto;
		width: calc(var(--dimension-1440) - var(--dimension-64));
	}

	.container {
		margin-right: var(--dimension-512);
	}

	.title {
		margin-right: var(--dimension-32);
		font-weight: var(--font-weight-bold);
		text-decoration: none;
	}


	.nav-links a[aria-current="page"] {
		color: var(--color-accent);
	}

	.nav-links > a {
		color: var(--color-base);
		margin-right: var(--dimension-16);
		text-decoration: none;
	}

	.theme-button::before {
		content: "|";
		padding-right: 10px;
		opacity: 10%;
	}

	.theme-button::after {
		content: "|";
		padding-left: 10px;
		opacity: 10%;
	}

	.theme-toggle {
		background: none;
		border: none;
		padding: 0;
		cursor: pointer;
		align-items: center;
		vertical-align: middle;
		justify-content: center;
		transition: all 0.2s ease;
	}

	.toggle-track {
		width: 32px;
		height: 16px;
		border-radius: 8px;
		position: relative;
		transition: all 0.3s ease;
		
		background: var(--bgn-surface);
		border: 1px solid var(--bgn-base);
	}

	.theme-toggle.dark .toggle-track {
		background: var(--bgn-surface);
		border: 1px solid var(--bgn-base);
	}

	.toggle-thumb {
		width: 12px;
		height: 12px;
		border-radius: 7px;
		position: absolute;
		top: 2px;
		left: 2px;
		display: flex;
		align-items: center;
		justify-content: center;
		transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
		
		background: var(--bgn-surface);
		color: var(--color-base);
		box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
	}

	.toggle-thumb.dark {
		transform: translateX(16px);
		background: var(--bgn-base);
		color: var(--color-base);
	}

	.theme-toggle:hover .toggle-track {
		border-color: var(--color-accent);
	}

	.theme-toggle:focus {
		outline: 2px solid var(--color-accent);
		outline-offset: 2px;
		border-radius: 10px;
	}

	/* Animação suave dos ícones */
	.toggle-thumb svg {
		transition: all 0.2s ease;
	}

	.github-link {
		vertical-align: sub;
	}

	.github-link img {
		color: red;
	}

</style>