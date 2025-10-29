<script lang="ts">
	import { onMount, onDestroy } from 'svelte';

	let tooltipVisible: boolean = false;

	const tooltipId: string = `atl-tooltip-${Math.random().toString(36).slice(2, 8)}`;

	let isTouch: boolean = false;

	export let text: string = '';
	export let direction:
		| 'top'
		| 'top-start'
		| 'top-end'
		| 'bottom'
		| 'bottom-start'
		| 'bottom-end'
		| 'left'
		| 'left-start'
		| 'left-end'
		| 'right'
		| 'right-start'
		| 'right-end' = 'bottom';

	let triggerEl: HTMLElement;

	function showTooltip() {
		tooltipVisible = true;
	}

	function hideTooltip() {
		tooltipVisible = false;
	}

	function onKeyDown(event: KeyboardEvent) {
		if (event.key === 'Escape') {
			hideTooltip();
		}
	}

	function onDocumentClick(event: MouseEvent) {
		if (!triggerEl.contains(event.target as Node)) {
			hideTooltip();
		}
	}

	function handleTouchStart() {
		isTouch = true;
		showTooltip();
	}

	function handleTouchEnd() {
		
	}

	function handleMouseEnter() {
		if (!isTouch) showTooltip();
	}

	function handleMouseLeave() {
		if (!isTouch) hideTooltip();
	}

	function handleFocus() {
		if (!isTouch) showTooltip();
	}

	function handleBlur() {
		if (!isTouch) hideTooltip();
	}

	onMount(() => {
		if (typeof document !== 'undefined') {
			document.addEventListener('keydown', onKeyDown);
			document.addEventListener('click', onDocumentClick);
		}
	});

	onDestroy(() => {
		if (typeof document !== 'undefined') {
			document.removeEventListener('keydown', onKeyDown);
			document.removeEventListener('click', onDocumentClick);
		}
	});

	const info = `<svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M7.75 0C3.47009 0 0 3.47134 0 7.75C0 12.0312 3.47009 15.5 7.75 15.5C12.0299 15.5 15.5 12.0312 15.5 7.75C15.5 3.47134 12.0299 0 7.75 0ZM7.75 3.4375C8.47487 3.4375 9.0625 4.02513 9.0625 4.75C9.0625 5.47487 8.47487 6.0625 7.75 6.0625C7.02513 6.0625 6.4375 5.47487 6.4375 4.75C6.4375 4.02513 7.02513 3.4375 7.75 3.4375ZM9.5 11.375C9.5 11.5821 9.33209 11.75 9.125 11.75H6.375C6.16791 11.75 6 11.5821 6 11.375V10.625C6 10.4179 6.16791 10.25 6.375 10.25H6.75V8.25H6.375C6.16791 8.25 6 8.08209 6 7.875V7.125C6 6.91791 6.16791 6.75 6.375 6.75H8.375C8.58209 6.75 8.75 6.91791 8.75 7.125V10.25H9.125C9.33209 10.25 9.5 10.4179 9.5 10.625V11.375Z" fill="var(--color-base)"/></svg>`;
</script>


<div class="atl-tooltip" on:mouseenter={handleMouseEnter} on:mouseleave={handleMouseLeave} role="group" aria-roledescription="Tooltip">
   <div
	   class="unstyled-button"
	   bind:this={triggerEl}
	   on:focus={handleFocus}
	   on:blur={handleBlur}
	   on:touchstart={handleTouchStart}
	   on:touchend={handleTouchEnd}
	   aria-describedby={tooltipId}
	   tabindex="0"
	   role="button">
	   <slot />
	   {#if !$$slots.default}
             {@html info}
        {/if}
   </div>

   {#if tooltipVisible}
	   <span
		   id={tooltipId}
		   role="tooltip"
		   class="tooltip-text {direction}"
		   aria-hidden={!tooltipVisible}
	   >
		   {text}
	   </span>
   {/if}
</div>

<style>

	@import url(../../style/global.css);

	.unstyled-button {
		all: unset;
		cursor: pointer;
		display: inline-flex;
		align-items: center;
		justify-content: center;
	}

	.atl-tooltip {
		position: relative;
		display: inline-block;
	}

	.tooltip-text {
		position: absolute;
		background-color: var(--color-base);
		color: var(--color-inverse);
		padding: var(--spacing-8) var(--spacing-4);
		font-size: var(--font-size-12);
		line-height: var(--line-height-label);
		white-space: nowrap;
		border-radius: var(--border-radius-4);
		z-index: 10;
		transition: opacity 0.2s ease;
		opacity: 1;
		pointer-events: none;
	}

	.tooltip-text.top {
		bottom: 100%;
		left: 50%;
		transform: translateX(-50%) translateY(calc(-1 * var(--spacing-8)));
	}
	.tooltip-text.top-start {
		bottom: 100%;
		left: 0;
		transform: translateY(calc(-1 * var(--spacing-8)));
	}
	.tooltip-text.top-end {
		bottom: 100%;
		right: 0;
		transform: translateY(calc(-1 * var(--spacing-8)));
	}

	.tooltip-text.bottom {
		top: 100%;
		left: 50%;
		transform: translateX(-50%) translateY(var(--spacing-8));
	}
	.tooltip-text.bottom-start {
		top: 100%;
		left: 0;
		transform: translateY(var(--spacing-8));
	}
	.tooltip-text.bottom-end {
		top: 100%;
		right: 0;
		transform: translateY(var(--spacing-8));
	}

	.tooltip-text.left {
		top: 50%;
		right: 100%;
		transform: translateY(-50%) translateX(calc(-1 * var(--spacing-8)));
	}
	.tooltip-text.left-start {
		top: 0;
		right: 100%;
		transform: translateX(calc(-1 * var(--spacing-8)));
	}
	.tooltip-text.left-end {
		bottom: 0;
		right: 100%;
		transform: translateX(calc(-1 * var(--spacing-8)));
	}

	.tooltip-text.right {
		top: 50%;
		left: 100%;
		transform: translateY(-50%) translateX(var(--spacing-8));
	}
	.tooltip-text.right-start {
		top: 0;
		left: 100%;
		transform: translateX(var(--spacing-8));
	}
	.tooltip-text.right-end {
		bottom: 0;
		left: 100%;
		transform: translateX(var(--spacing-8));
	}
</style>