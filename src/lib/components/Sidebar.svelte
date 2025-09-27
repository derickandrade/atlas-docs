<!-- src/lib/Sidebar.svelte -->
<script lang="ts">
  import { page } from '$app/state';

  type Section = {
    title?: string;
    items: { href: string; label: string }[];
  };

  export let sections: Section[] = []; // [{ title?, items: [{ href, label }] }]
</script>

<nav class="sidebar">
    <div class="div-line"></div>
  {#each sections as section}
    <div class="section">
      {#if section.title}
        <h2>{section.title}</h2>
      {/if}

      <ul>
        {#each section.items as { href, label }}
          <li class="link-item">
            <a
              href={href}
              class:active={page.url.pathname === href}
            >
              {label}
            </a>
          </li>
        {/each}
      </ul>
    </div>
    <div class="div-line"></div>
  {/each}
</nav>

<style>
.sidebar {
  width: 15%;
  background: var(--bgn-base);
  padding: 1rem;
  border-right: 1px solid var(--bgn-surface);
  position: fixed;
  height: 100vh;
}

.div-line {
    opacity: 40%;
    height: 1px;
    background-color: var(--bgn-surface);
    margin: var(--dimension-8) 0;
}

.link-item {
    margin: var(--dimension-16) 0;
}

h2 {
  font-size: var(--dimension-16);
  font-weight: var(--font-weight-bold);
  margin-bottom: var(--dimension-16);
}

ul {
  list-style: none;
  padding: 0;
}

a {
  text-decoration: none;
  color: var(--color-base);
}

a.active {
  font-weight: bold;
  color: var(--color-accent);
}

@media screen and (max-width: 1439px) {
  .sidebar {
    width: min(200px, 20%);
  }
}

</style>
