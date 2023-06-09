<script>
    // Due to the location that Evidence builds the site, we need to hop up many directories to get to root
    import FranceMap from "../../../../../src/lib/charts/maps/FranceMap.svelte";
</script>

```sql france
select 'Gironde' as department, 1000 as sales
union all
select 'Cantal' as department, 2000 as sales
union all
select 'Loir-et-Cher' as department, 888 as sales
union all
select 'Seine-et-Marne' as department, 485 as sales
union all
select 'Morbihan' as department, 294 as sales
union all
select 'Vendée' as department, 998 as sales
```

```sql world
select 'Canada' as country, 100 as sales_usd
union all
select 'United Kingdom' as country, 50 as sales_usd
union all
select 'France' as country, 200 as sales_usd
union all
select 'Argentina' as country, 150 as sales_usd
union all
select 'Mexico' as country, 150 as sales_usd
union all
select 'Chad' as country, 65 as sales_usd
union all
select 'Germany' as country, 70 as sales_usd
union all
select 'Egypt' as country, 17 as sales_usd
union all
select 'Greenland' as country, 55 as sales_usd
union all
select 'China' as country, 155 as sales_usd
```




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