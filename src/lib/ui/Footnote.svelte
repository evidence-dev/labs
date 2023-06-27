<script context="module">
    export const evidenceInclude = true;
</script>

<script>
    export let id = undefined;
</script>

<div class=footnote>
    {#if id}
    <div class=footnote-id>
        <sup>{id} </sup>
    </div>
    {/if}

    <slot></slot>
</div>

<style>
    .footnote {
        font-size: 10pt;
        color: var(--grey-600);
        margin-left: 5px;
        margin-right: 10px;
        margin-bottom: 25px;
        margin-top: -10px;
    }

    .footnote-id {
        display: inline-block;
    }
</style>