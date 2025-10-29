<script>

</script>

<div class="tabs" role="tablist" aria-selected="true" aria-controls="" >
    <a href="#" class="tab"tabindex=0>Tab</a>
    <a href="#" class="tab select" tabindex=0>Tab</a>
    <a href="#" class="tab disable"tabindex=-1>Tab</a>
    <a href="#" class="tab"tabindex=0>Tab</a>
    <a href="#" class="tab"tabindex=0>Tab</a>
    <a href="#" class="tab"tabindex=0>Tab</a>
</div>

<style>
    @import url(../../style/global.css);

    .tabs {
        width: fit-content;
        font-size: var(--font-size-14);
        font-weight: 600;
        display: flex;
        flex-direction: row;
    }

    .tab {
        display: flex;
        align-items: last baseline;
        height: 38px;
        border-top-left-radius: 4px;
        border-top-right-radius: 4px;
        padding: 0 16px 8px 16px;
        text-decoration: none;
        border-bottom: 2px solid var(--color-subtle);
        margin: 0;
    }

    .tab:hover {
        background-color: var(--bgn-disable);
        border-bottom: 2px solid var(--bgn-disable);
    }

    .select {
        border-bottom: 3px solid var(--color-accent);
    }

    .tab.select:hover {
        color: var(--color-accent-hover);
        background-color: var(--bgn-foreground);
        border-bottom: 3px solid var(--color-accent);
    }

    .tab:focus {
        outline: none;
        border-bottom: 3px solid var(--color-accent);
        border-bottom-left-radius: 0px;
        border-bottom-right-radius: 0px;
    }

    .select.tab:focus {
        outline: 2px solid var(--color-accent);
        border-bottom: none;
        border-radius: 4px;
    }

    .disable {
        pointer-events: none;
        color: var(--bgn-disable);
        border-bottom: 2px solid var(--bgn-base);
    }

</style>