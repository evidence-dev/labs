<script context="module">
    export const evidenceInclude = true;
</script>

<script>
    export let columns = 2;
    columns = parseInt(columns);

    export let gapWidth = 10;
</script>

<div class=grid style="display: grid; grid-template-columns: repeat({columns}, minmax(0, 1fr)); column-gap: {gapWidth}px;">
    <slot></slot>
</div>

<style>
    @media screen and (max-width: 480px) {
        .grid {
            grid-template-columns: auto !important;
        }
	}
</style>