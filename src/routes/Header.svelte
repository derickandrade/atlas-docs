<script lang="ts">
	import { page } from '$app/state';
	import { onMount } from 'svelte';

	let isDarkMode: boolean = false;
	let isSideNavbarOpen: boolean = false;

	$: currentPath = page.url?.pathname;

	onMount(() => {
		
		const savedTheme = localStorage.getItem('theme');
		const systemPrefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
		const media = window.matchMedia("(width < 1440px");
		const navLinks = document.querySelectorAll('nav a');
		navLinks.forEach(link => {
			link.addEventListener('click', () => {
				isSideNavbarOpen = false;
			})
		})
		updateNavbar(media);
		isDarkMode = savedTheme === 'dark' || (!savedTheme && systemPrefersDark);
		updateTheme();
		document.addEventListener('keydown', handleKeydown);
		media.addEventListener('change', (e) => updateNavbar(e))
		attCurrentPage();
	});

	function attCurrentPage() {
		const navLinks = document.querySelectorAll('nav a');
		navLinks.forEach(link => {
			if (link.getAttribute('href') === currentPath) {
				link.classList.add('active-link');
				link.setAttribute('aria-current', 'page');
			} else {
				link.classList.remove('active-link');
				link.removeAttribute('aria-current');
			}
		});
	}

	function toggleTheme() {
		isDarkMode = !isDarkMode;
		updateTheme();
		localStorage.setItem('theme', isDarkMode ? 'dark' : 'light');
	}

	function updateTheme() {
		if (isDarkMode) {
			document.documentElement.style.colorScheme = 'dark';
		} else {
			document.documentElement.style.colorScheme = 'light'
		}
	}

	function updateNavbar(e: MediaQueryListEvent | MediaQueryList) {
		const isMobile = e.matches
		if (isMobile) {
			document.getElementById('hidden-menu')?.setAttribute('inert', '');
		}
		else {
			document.getElementById('hidden-menu')?.removeAttribute('inert');
		}
	}

	function sideNavbar() {
		isSideNavbarOpen = !isSideNavbarOpen;
		if (isSideNavbarOpen) {
			document.getElementById('side-navbar-button')?.setAttribute('aria-expanded', 'true');
			document.getElementById('menu-hidden')?.setAttribute('aria-hidden', 'false');
			document.getElementById('hidden-menu')?.removeAttribute('inert');
			
		}
		else {
			document.getElementById('side-navbar-button')?.setAttribute('aria-exapanded', 'false');
			document.getElementById('menu-hidden')?.setAttribute('aria-hidden', 'true');
			document.getElementById('hidden-menu')?.setAttribute('inert', '');
		}
	}

	function handleKeydown(e: KeyboardEvent) {
		if (e.key === 'Escape') {
			sideNavbar();
		}
	}

</script>

<header>
	<span></span>
	<nav class="nav">
        <ul id="visible-menu">
			<li aria-label="Home Button"><a id="home" class="active-link" href="/" class:active={page.url.pathname === '/'} aria-current={currentPath === '/' ? 'page' : undefined}>Atlas</a></li>
			<li class="left-menu"><button id="search-button"><svg id="magnifier" xmlns="http://www.w3.org/2000/svg" height="18px" viewBox="0 -960 960 960" width="18px" fill="#c9c9c9"><path d="M784-120 532-372q-30 24-69 38t-83 14q-109 0-184.5-75.5T120-580q0-109 75.5-184.5T380-840q109 0 184.5 75.5T640-580q0 44-14 83t-38 69l252 252-56 56ZM380-400q75 0 127.5-52.5T560-580q0-75-52.5-127.5T380-760q-75 0-127.5 52.5T200-580q0 75 52.5 127.5T380-400Z"/></svg>Search</button></li>
		</ul>

		<button id="side-navbar-button" on:click={sideNavbar} aria-label="Navigation Bar Menu" aria-expanded='false' aria-controls="hidden-menu">
			<span id="showMenu" class:show={isSideNavbarOpen}>
				<svg xmlns="http://www.w3.org/2000/svg" height="25px" viewBox="0 -960 960 960" width="25px" fill="var(--color-base)"><path d="M144-264v-72h672v72H144Zm0-180v-72h672v72H144Zm0-180v-72h672v72H144Z"/></svg>
			</span>
			<span id="closeMenu" class:show={isSideNavbarOpen}>
				<svg xmlns="http://www.w3.org/2000/svg" height="25px" viewBox="0 -960 960 960" width="25px" fill="var(--color-base)"><path d="m291-240-51-51 189-189-189-189 51-51 189 189 189-189 51 51-189 189 189 189-51 51-189-189-189 189Z"/></svg>
			</span>
		</button>
		
		<ul id="hidden-menu" class="hidden-menu" class:show={isSideNavbarOpen} aria-hidden='true'>
			<li></li>
            <li><a href="#">Using Atlas</a></li>
            <li><a href="#">Contributing</a></li>
            <li><a href="#">Style Guide</a></li>
            <li><a  href="#">Design Tokens</a></li>
            <li><a class:active={page.url.pathname.startsWith("/components")} href="/components/overview">Components</a></li>
            <li class="theme-li"><button id="theme-button" on:click={toggleTheme}>
				<span id="theme-icon">
					<svg id="sun" xmlns="http://www.w3.org/2000/svg" height="16px" viewBox="0 -960 960 960" width="16px" fill="var(--color-base)"><path d="M480-360q50 0 85-35t35-85q0-50-35-85t-85-35q-50 0-85 35t-35 85q0 50 35 85t85 35Zm0 80q-83 0-141.5-58.5T280-480q0-83 58.5-141.5T480-680q83 0 141.5 58.5T680-480q0 83-58.5 141.5T480-280ZM200-440H40v-80h160v80Zm720 0H760v-80h160v80ZM440-760v-160h80v160h-80Zm0 720v-160h80v160h-80ZM256-650l-101-97 57-59 96 100-52 56Zm492 496-97-101 53-55 101 97-57 59Zm-98-550 97-101 59 57-100 96-56-52ZM154-212l101-97 55 53-97 101-59-57Zm326-268Z"/></svg>
					<svg id="moon" xmlns="http://www.w3.org/2000/svg" height="16px" viewBox="0 -960 960 960" width="16px" fill="#c9c9c9"><path d="M480-120q-150 0-255-105T120-480q0-150 105-255t255-105q14 0 27.5 1t26.5 3q-41 29-65.5 75.5T444-660q0 90 63 153t153 63q55 0 101-24.5t75-65.5q2 13 3 26.5t1 27.5q0 150-105 255T480-120Zm0-80q88 0 158-48.5T740-375q-20 5-40 8t-40 3q-123 0-209.5-86.5T364-660q0-20 3-40t8-40q-78 32-126.5 102T200-480q0 116 82 198t198 82Zm-10-270Z"/></svg>
				</span>
			</button></li>
            <li><a id="github-link" href="https://github.com/OSMBrasil/design-atlas" target="_blank" rel="_external"><svg width="24" height="24" viewBox="0 0 97.707 97.707" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" clip-rule="evenodd" d="M48.854 0C21.839 0 0 22 0 49.217c0 21.756 13.993 40.172 33.405 46.69 2.427.49 3.316-1.059 3.316-2.362 0-1.141-.08-5.052-.08-9.127-13.59 2.934-16.42-5.867-16.42-5.867-2.184-5.704-5.42-7.17-5.42-7.17-4.448-3.015.324-3.015.324-3.015 4.934.326 7.523 5.052 7.523 5.052 4.367 7.496 11.404 5.378 14.235 4.074.404-3.178 1.699-5.378 3.074-6.6-10.839-1.141-22.243-5.378-22.243-24.283 0-5.378 1.94-9.778 5.014-13.2-.485-1.222-2.184-6.275.486-13.038 0 0 4.125-1.304 13.426 5.052a46.97 46.97 0 0 1 12.214-1.63c4.125 0 8.33.571 12.213 1.63 9.302-6.356 13.427-5.052 13.427-5.052 2.67 6.763.97 11.816.485 13.038 3.155 3.422 5.015 7.822 5.015 13.2 0 18.905-11.404 23.06-22.324 24.283 1.78 1.548 3.316 4.481 3.316 9.126 0 6.6-.08 11.897-.08 13.526 0 1.304.89 2.853 3.316 2.364 19.412-6.52 33.405-24.935 33.405-46.691C97.707 22 75.788 0 48.854 0z" fill="var(--color-base)"/></svg></a></li>
        </ul>
	</nav>
</header>

<div id="overlay" class:show={isSideNavbarOpen} on:click={sideNavbar} on:keypress={handleKeydown} aria-hidden="true"></div>

<style>
	@import '../style/global.css';

	#theme-button {
		align-self: center;
		width: 50px;
		position: relative;
		height: 28px;
		border-radius: 14px;
		border: 1px solid var(--color-base);
		margin: 0 1rem;
	}

	#theme-button:hover {
		background-color: var(--bgn-surface-hover);
		border-color: var(--color-accent);
	}

	#sun {
		display: block;
	}

	#moon {
		display: none;
	}

	:root[style*="color-scheme: dark"] #sun {
		display: none;
	}

	:root[style*="color-scheme: dark"] #moon {
		display: block;
	}
	

	#theme-icon {
		position: absolute;
		transform: translateY(-50%);
		left: 0;
		background-color: var(--bgn-surface);
		border-radius: 50%;
		display: flex;
		justify-content: center;
		padding: 3px;
		transition: all 300ms ease;
		margin-left: 1px;	
	}


	:root[style*="color-scheme: dark"] #theme-icon {
		left: auto;
		transform: translateX(100%) translateY(-50%);
	}

	nav {
		display: flex;
		position: fixed;
		z-index: 10;
		background-color: var(--bgn-surface);
		width: 100%;
		height: 2.5em;
	}

	nav ul {
		list-style: none;
		display: flex;
	}

	#home:hover {
		font-weight: inherit;
	}

	nav a {
		font-size: 1rem;
		display: flex;
		text-decoration: none;
		padding: 10px 15px;
		transition: background-color 150ms ease;
		&:hover {
			font-weight: var(--font-weight-semibold);
		}
	}

	nav li {
		display: flex;
	}

	nav a:focus {
		border: var(--border-style-active);
	}

	a.active {
		color: var(--color-accent);
		font-weight: 700;
	}

	#visible-menu {
		display: flex;
		margin-right: auto;
		padding-left: 2em;
	}

	#side-navbar-button {
		display: none;
		padding-top: 0.5em;
		border: none;
		padding-right: 1rem;
		background-color: transparent;
	}

	#overlay {
		background-color: rgba(0, 0, 0, 0.5);
		position: fixed;
		inset: 0;
		z-index: 9;
		display: none;
	}

	ul.hidden-menu {
		padding-right: 1.5rem;
	}

	#search-button {
		width: 200px;
		margin: 5px 0 5px 3rem;
		position: relative;

		&:hover {
			border: 1px solid var(--color-accent);
			border-radius: 4px;
		}
	}

	#search-button:hover #magnifier{
		fill: var(--color-accent);
	}

	#magnifier {
		margin: 0 0.5rem;
		position: absolute;
		left: 0;
		
	}
	
	@media screen and (max-width: 1439px) {

		li.theme-li::before{
			display: flex;
			content: 'Theme:';
			padding: 10px 0 10px 1rem;
			color: var(--color-base);
		}

		#side-navbar-button {
			display: block;
		}

		#showMenu.show svg {
			display: none;
		}

		#closeMenu svg {
			display: none;
		}

		#closeMenu.show svg {
			display: block;
		}

		
		.hidden-menu {
			position: fixed;
			right: 0;
			top: -100%;
			height: auto;
			padding-bottom: 1rem;
			border-radius: 0 0 0 var(--border-radius-8);
			width: min(12em, 26%);
			z-index: 10;
			flex-direction: column;
			background-color: var(--bgn-surface);
			transition: top 350ms ease-out;
		}

		.hidden-menu a {
			width: 100%;
			padding-left: 1em;
		}

		#github-link {
			margin-left: auto;
		}

		.hidden-menu.show {
			top: 2.5em;

			#open-sidenavbar-button {
				display: none;
			}
			
			#close-sidenavbar-button {
				display: block;
			}

		}

		#overlay.show {
			display: block;
		}
	}

</style>