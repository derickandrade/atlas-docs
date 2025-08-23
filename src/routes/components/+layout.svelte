<script lang="ts">
	import '../../app.css';
	import Sidebar from '$lib/components/Sidebar.svelte'; '../../lib/components/Sidebar.svelte'

	let { children } = $props();

	const sidebarLinks = [
		{
			title: "Componentes",
			items: [
				{ href: "/components/overview", label: "Overview"}
			]
		},
		{	
			items: [
				{ href: "#", label: "Accordion"},
				{ href: "#", label: "Alert" },
				{ href: "/components/button", label: "Button" },
			]
		}
	];
</script>

<div class="app">
	<Sidebar sections={sidebarLinks}></Sidebar>

	<main>
		{@render children()}
	</main>

	
</div>

<style>
	.app {
		display: flex;
		min-height: 100vh;
	}

	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 5rem 1rem;
		width: 100%;
		max-width: 100rem;
		margin: 0 auto;
		display: flex;
	}

</style>
