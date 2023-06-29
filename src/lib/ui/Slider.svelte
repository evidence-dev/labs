<script context="module">
    export const evidenceInclude = true;
</script>

<script>
	// export makes the variable a component property	
	export let value;

    export let min = 0;
    export let max = 10;
    export let step = 1;
</script>

<input type='range' bind:value min={min} max={max} step={step} />