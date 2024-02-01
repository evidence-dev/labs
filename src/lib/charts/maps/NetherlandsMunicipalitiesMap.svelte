<script context="module">
    export const evidenceInclude = true;
</script>

<script>
    import CustomMapConfig from './CustomMapConfig.svelte';
    import mapJson from './georef-netherlands-gemeente@public.json';

    export let mapName = 'NetherlandsMunicipalities'; // used to define distinct map name for ECharts

    // Map these props to the property names in the JSON file:
    export let nameProperty = 'gem_name';
    export let abbreviationProperty = undefined;
    export let abbreviations = false;

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