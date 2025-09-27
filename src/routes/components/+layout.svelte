<script lang="ts">
	import '../../app.css';
	import Sidebar from '$lib/components/Sidebar.svelte'; '../../lib/components/Sidebar.svelte'

	let { children } = $props();

	const sidebarLinks = [
		{
			title: "Components",
			items: [
				{ href: "/components/overview", label: "Overview"}
			]
		},
		{	
			items: [
				{ href: "/components/accordion", label: "Accordion"},
				{ href: "/components/alert", label: "Alert" },
				{ href: "/components/button", label: "Button" },
			]
		}
	];
</script>

<div class="app">
	<span id="sidebar">
		<Sidebar sections={sidebarLinks}></Sidebar>
	</span>

	<main>
		{@render children()}
	</main>

	
</div>

<style>

	@import url('../../app.css');

	.app {
		display: flex;
		min-height: 100vh;
	}

	main {
		flex: 1;
		flex-direction: column;
		width: 100%;
		max-width: min(900px, 90%);
		margin-left: 20%;
		margin-right: 15%;
		overflow-y: auto;
		padding: 2rem;
	}

	:global(h1) {
		text-align: left;
		font-size:  var(--font-size-60, 3.75rem);
	}

	:global(h2) {
		font-size: var(--font-size-48, 3rem);
		padding-top: var(--dimension-32);
	}

	:global(h3) {
		font-size: var(--font-size-40, 2.5rem);
		padding-top: var(--dimension-32);
	}

	:global(h4) {
		font-size: var(--font-size-32, 2rem);
		padding-top: var(--dimension-32);
	}

	:global(p) {
		text-align: justify;
		max-width: var(--dimension-800);
		padding: var(--dimension-16) 0;
	}

	:global(aside::before) {
		content: "On this page";
		font-weight: var(--font-weight-bold);
		font-size: var(--dimension-12);
	}

	:global(aside) {
		position: fixed;
		top: 15%;
		left: 83%;
		
		font-size: var(--dimension-12);
	}

	:global(aside > ul) {
		list-style-type: none;
	}

	:global(aside > ul > li) {
		text-overflow: clip;
		padding: 3px 0;
		line-height: 1.5;
	}

	:global(ul.list-dos, ol.list-numbers) {
		list-style-position: inside;
		margin: var(--dimension-8) 0;
	}

	:global(ul.list-dos > li, ol.list-numbers > li) {
		padding: var(--dimension-4) 0;
	}

	:global(.prop) {
		font-family: monospace;
		background-color: var(--bgn-surface);
		padding: var(--dimension-4) var(--dimension-8);
		border-radius: var(--dimension-4);
		font-size: var(--dimension-12);
		color: var(--color-accent);
		&#warning {
			background-color: var(--bgn-surface);
			color: var(--color-warning);
		}
	}

	:global(#div-line) {
		opacity: 60%;
		height: 1px;
		background-color: var(--bgn-surface);
		margin: var(--dimension-16) 0;
	}

	:global(.note::before) {
		content: "Note:";
		display: block;
		font-weight: var(--font-weight-bold);
	}

	:global(.note) {
		background-color: var(--bgn-info);
		border-radius: var(--dimension-8);
		padding: var(--dimension-16);
		margin: var(--dimension-16) 0;
		font-size: var(--dimension-12);
	}

	:global(.warning::before) {
		content: "WARNING";
		display: block;
		font-weight: var(--font-weight-bold);
	}

	:global(.warning) {
		background-color: var(--bgn-warning);
		border-radius: var(--dimension-8);
		padding: var(--dimension-16);
		margin: var(--dimension-16) 0;
		font-size: var(--dimension-12);
	}

	@media screen and (max-width: 1439px) {
		main {
			position: relative;
			margin-left: min(20%, 210px);
		}

		:global(aside) {
			top: 7%;
			right: 7%;
		}
	}

</style>
