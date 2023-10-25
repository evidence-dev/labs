---
sources:
- france.sql
- world.sql
---



<script>
    // Due to the location that Evidence builds the site, we need to hop up many directories to get to root
    import FranceMap from "../../../../../src/lib/charts/maps/FranceMap.svelte";
    import WorldMap from "../../../../../src/lib/charts/maps/WorldMap.svelte";
</script>




# Maps

## France Map

<FranceMap 
    data={france} 
    region=department 
    value=sales 
/>

```html
<FranceMap 
    data={france} 
    region=department 
    value=sales 
/>
```

## Green Map with Title and Subtitle

<FranceMap 
    title="Sales by Department"
    subtitle="000s €"
    data={france} 
    region=department 
    value=sales 
    colorScale=green
/>

```html
<FranceMap 
    title="Sales by Department"
    subtitle="000s €"
    data={france} 
    region=department 
    value=sales 
    colorScale=green 
/>
```

## Map with Links

<FranceMap
    data={france}
    region=department
    value=sales
    link=department
/>

```html
<FranceMap
    data={france}
    region=department
    value=sales
    link=department
/>
```

## World Map

<WorldMap 
    data={world} 
    title="World Map" 
    subtitle="Sales by Country" 
    region=country 
    value=sales_usd 
    colorScale=green
/>

```html
<WorldMap 
    data={world} 
    title="World Map" 
    subtitle="Sales by Country" 
    region=country 
    value=sales_usd 
    colorScale=green
/>
```