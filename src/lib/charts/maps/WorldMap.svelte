<script>
    import CustomMapConfig from './CustomMapConfig.svelte';
    import mapJson from './worldMap.json';

    export let mapName = 'World';

    export let data;

    // Set names for region and value props:
    export let region;
    export let value;

    export let min = undefined;
	export let max = undefined;

	export let title = undefined;
	export let subtitle = undefined;

	export let link = undefined;

	export let colorScale = undefined;

    export let nameProperty = 'name'
    export let abbreviationProperty = undefined;
    export let abbreviations = false;

</script>


<CustomMapConfig 
    {mapJson} 
    {data}
    {mapName} 
    {region} 
    {value}
    {min}
    {max}
    {title}
    {subtitle}
    {link}
    {colorScale}
    {nameProperty}
    {abbreviationProperty}
    {abbreviations}
/>