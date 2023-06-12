<script>
    // Due to the location that Evidence builds the site, we need to hop up many directories to get to root
    import FranceMap from "../../../../../src/lib/charts/maps/FranceMap.svelte";
</script>

```sql france
select 'Gironde'            as department, 1000 as sales union all
select 'Cantal'             as department, 2000 as sales union all
select 'Loir-et-Cher'       as department, 888 as sales union all
select 'Seine-et-Marne'     as department, 485 as sales union all
select 'Morbihan'           as department, 294 as sales union all
select 'Vendée'             as department, 998 as sales union all
select 'Haute-Savoie'       as department, 100 as sales union all
select 'Haute-Garonne'      as department, 200 as sales union all
select 'Ardèche'            as department, 300 as sales union all
select 'Aude'               as department, 400 as sales union all
select 'Aveyron'            as department, 500 as sales union all
select 'Bouches-du-Rhône'   as department, 600 as sales union all
select 'Calvados'           as department, 700 as sales union all
select 'Charente'           as department, 800 as sales union all
select 'Charente-Maritime'  as department, 900 as sales union all
select 'Corrèze'            as department, 1000 as sales union all
select 'Côtes-d\'Armor'     as department, 123 as sales union all
select 'Creuse'             as department, 852 as sales union all
select 'Dordogne'           as department, 741 as sales union all
select 'Doubs'              as department, 963 as sales union all
select 'Drôme'              as department, 852 as sales union all
select 'Eure'               as department, 235 as sales union all
select 'Eure-et-Loir'       as department, 741 as sales union all
select 'Finistère'          as department, 852 as sales union all
select 'Gard'               as department, 416 as sales union all
select 'Haute-Garonne'      as department, 749 as sales union all
select 'Gers'               as department, 787 as sales union all
select 'Hérault'            as department, 74 as sales union all
select 'Ille-et-Vilaine'    as department, 665 as sales union all
select 'Indre'              as department, 417 as sales union all
select 'Indre-et-Loire'     as department, 111 as sales union all
select 'Isère'              as department, 222 as sales union all
select 'Jura'               as department, 333 as sales union all
select 'Landes'             as department, 456 as sales union all
select 'Loir-et-Cher'       as department, 789 as sales union all
select 'Loire'              as department, 741 as sales union all
select 'Haute-Loire'        as department, 852 as sales union all
select 'Loire-Atlantique'   as department, 963 as sales union all
select 'Loiret'             as department, 741 as sales union all
select 'Lot'                as department, 852 as sales union all
select 'Lot-et-Garonne'     as department, 963 as sales union all
select 'Lozère'             as department, 741 as sales union all
select 'Maine-et-Loire'     as department, 852 as sales union all
select 'Manche'             as department, 963 as sales union all
select 'Paris'              as department, 2154 as sales union all
select 'Seine-Maritime'     as department, 741 as sales union all
select 'Seine-Saint-Denis'  as department, 852 as sales
```

```sql world
select 'Canada' as country, 100 as sales_usd union all
select 'United Kingdom' as country, 50 as sales_usd union all
select 'France' as country, 200 as sales_usd union all
select 'Argentina' as country, 150 as sales_usd union all
select 'Mexico' as country, 150 as sales_usd union all
select 'Chad' as country, 65 as sales_usd union all
select 'Germany' as country, 70 as sales_usd union all
select 'Egypt' as country, 17 as sales_usd union all
select 'Greenland' as country, 55 as sales_usd union all
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