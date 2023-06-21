<script context="module">
    export const evidenceInclude = true;
</script>

<script>
    export let path = undefined;
    export let width = '100%';
    export let height = '400px';
    export let toolbar = true;
    toolbar = (toolbar === "true" || toolbar === true);
    let toolbarBool = toolbar ? 1 : 0;

    export let page = 1;

    let src = path + 
        "#toolbar=" + toolbarBool +
        "&page=" + page


</script>

{#if path}
<iframe class=pdf title={path} src="{src}" width="{width}" height="{height}"/>
{:else}
<code>path</code> to PDF file must be supplied
{/if}

<style>
    .pdf {
        border: 1px solid var(--grey-200);
        border-radius: 4px;
    }
</style>
