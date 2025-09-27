<script lang="ts">
    import AtlButton from '$lib/components/atl-button.svelte';
    
    let selectedVariant = 'primary';
    let isDisabled = false;
    let hasIcon = false;
    let buttonLabel = 'Click Me';
</script>

<div class="demo-container">
    <div class="preview">
        <AtlButton variant={selectedVariant} withIcon={hasIcon} disabled={isDisabled}>
            {buttonLabel}
        </AtlButton>
    </div>

    <div class="controls">
        
        <div class="control-group">
            <label for="variant">Variant</label>
            <div id="variant" class="radio-group">
                {#each ['primary', 'outline', 'tertiary', 'danger'] as v}
                    <label class="radio-label">
                        <input type="radio" value={v} bind:group={selectedVariant}>
                        {v}
                    </label>
                {/each}
            </div>
        </div>

        <div>
    <input id="disabled" type="checkbox" bind:checked={isDisabled}>
    <label for="disabled">Disabled</label>
</div>

<div>
    <input id="withIcon" type="checkbox" bind:checked={hasIcon}>
    <label for="withIcon">With Icon</label>
</div>

        <div class="control-group">
            <label for="button-label">Label</label>
            <input id="button-label" type="text" bind:value={buttonLabel}>
        </div>
    </div>
</div>

<style>
    
</style>