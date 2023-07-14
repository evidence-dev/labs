<script context="module">
    export const evidenceInclude = true;
</script>

<script>
    import { onMount, onDestroy } from 'svelte';
    import { browser } from '$app/environment';
    import formatTitle from '@evidence-dev/component-utilities/formatTitle'

    let mapElement;
    let map;

    export let data;
    export let lat;
    export let long;
    export let name;
    export let startingLat = 44.4;
    export let startingLong = 0.3;
    export let startingZoom = 13;
    export let tooltipFields = [];
    export let height = 500; // height in pixels


    $: onMount(async () => {
        if(browser) {
            const leaflet = await import('leaflet');

            map = leaflet.map(mapElement).setView([startingLat, startingLong], startingZoom);

            leaflet.tileLayer('https://{s}.basemaps.cartocdn.com/light_all/{z}/{x}/{y}{r}.png', {
                subdomains: 'abcd',
                maxZoom: 20
            }).addTo(map);

            let currentPoint;
            let prevPoint;
            let latLngData = [];
            let tooltipCode;
            for(let i=0; i < data.length; i++){
                latLngData.push([[data[i][lat], data[i][long]]]);
                currentPoint = [[data[i][lat], data[i][long]]];
                if(i > 0){
                    prevPoint = [[data[i-1][lat], data[i-1][long]]];
                }
                let marker = leaflet.marker([data[i][lat], data[i][long]]).addTo(map);

                tooltipCode = "";
                for(let j=0; j<tooltipFields.length; j++){
                    tooltipCode = tooltipCode + `<b>${formatTitle(tooltipFields[j])}</b>` + ": " + data[i][tooltipFields[j]] + "<br>"
                }
                marker.bindPopup(`<b>${data[i][name]}</b><br><span style="color: grey; font-size: 0.9em;">${tooltipCode}</span>`).openPopup();

                if(prevPoint !== undefined){
                    leaflet.polyline([prevPoint, currentPoint]).addTo(map);
                }
            }
            var bounds = leaflet.latLngBounds(latLngData);
            map.fitBounds(bounds);
            map.removeControl(map.attributionControl)

        }
    });

    $: data;

    $: onDestroy(async () => {
        if(map) {
            console.log('Unloading Leaflet map.');
            map.remove();
        }
    });
</script>


<main>
    <div style="height: {height}px;" bind:this={mapElement}></div>
</main>

<style>
    @import 'leaflet/dist/leaflet.css';
    main div {
        z-index: 0;
    }
</style>