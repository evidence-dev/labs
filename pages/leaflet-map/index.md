<script>
    // Due to the location that Evidence builds the site, we need to hop up many directories to get to root
    import LeafletMap from "../../../../../src/lib/charts/maps/LeafletMap.svelte";
</script>

# Leaflet Map

- This map plots markers on an interactive map using latitude and longitude columns
- A customizable tooltip is included by passing column names in an array
- Does not support value formatting yet
- Auto-zooms to the points plotted on the map

```coords
select 51.51123691095239 as lat,  -0.13465819567340626 as long, 'London' as city, 'Bobs' as store_name, 44345 as annual_sales, 'SMB' as segment
union all
select 51.51153241529485 as lat, -0.13175192134263558 as long, 'London' as city, 'Bills' as store_name, 55344 as annual_sales, 'SMB' as segment
union all
select 51.51204873146856 as lat, -0.1302492157640683 as long, 'London' as city, 'The Fox and Badger' as store_name, 12342 as annual_sales, 'SMB' as segment
union all
select 51.51116547005441 as lat, -0.12908566248621936 as long, 'London' as city, 'One Day Plumbing' as store_name, 55245 as annual_sales, 'SMB' as segment
union all
select 51.51044456017838 as lat, -0.13666702083919927 as long, 'London' as city, 'Fenton Atheltic Apparel' as store_name, 63578 as annual_sales, 'SMB' as segment
```

```svelte
<LeafletMap 
    data={coords} 
    lat=lat 
    long=long
    name=store_name
    tooltipFields={['segment', 'annual_sales', 'city']}
    height=500
/>
```

<LeafletMap 
    data={coords} 
    lat=lat 
    long=long
    name=store_name
    tooltipFields={['segment', 'annual_sales', 'city']}
    height=500
/>

## Future Improvements
- Syntax should be expanded to allow for more flexibility and customization. E.g., allow for definitions of multiple sets and styles of markers, arbitrary shapes, choropleths, etc.
- Syntax may be similar to the DataTable with Columns. For example, if you wanted to show service locations, along with a service radius:
   ```svelte
      <LeafletMap basemap=cartoGrey>
        <Markers color=red data={high_value_locations} tooltipFields={['segment', 'annual_sales', 'city']} />
        <Markers color=blue data={low_value_locations} tooltipFields={['segment', 'annual_sales', 'city']} />
        <Circle centreLat=51.2342 centreLong=-0.1258 radius=2 label="Service Area" />
      </LeafletMap>
   ```
- Having a few off-the-shelf styles for markers/shapes would be helpful (like in `ReferenceArea`)
- Tooltip customization may require specific syntax - e.g., a `Tooltip` component that slots into the `Markers` component
- Like with DataTable, if there are common use cases, it might make sense to cover those in their own pre-set components which call the underlying LeafletMap component