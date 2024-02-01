---
sources:
- netherlands.sql
---



<script>
    // Due to the location that Evidence builds the site, we need to hop up many directories to get to root
    import NetherlandsMunicipalitiesMap from "../../../../../src/lib/charts/maps/NetherlandsMunicipalitiesMap.svelte";
</script>




# Maps

## Dutch Map

<NetherlandsMunicipalitiesMap 
    data={netherlands} 
    region=department 
    value=sales
/>

```html
<NetherlandsMunicipalitiesMap 
    data={netherlands} 
    region=department 
    value=sales 
/>
```
