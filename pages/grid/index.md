<script>
    // Due to the location that Evidence builds the site, we need to hop up many directories to get to root
    import Grid from "../../../../../src/lib/ui/Grid.svelte";
</script>

# Grid Component

```mock_data
select DATE '2023-01-31' as month, 1234 as value
union all
select DATE '2023-02-28' as month, 2344 as value
union all
select DATE '2023-03-31' as month, 2424 as value
union all
select DATE '2023-04-30' as month, 2454 as value
union all
select DATE '2023-05-31' as month, 3884 as value
```

## Section 1
<Grid columns=3 gapWidth=10>
    <LineChart data={mock_data}/>
    <BarChart data={mock_data}/>
    <DataTable data={mock_data}/>
</Grid>

```html
<Grid columns=3 gapWidth=10>
    <LineChart data={mock_data}/>
    <BarChart data={mock_data}/>
    <DataTable data={mock_data}/>
</Grid>
```

## Section 2
<Grid columns=2>
    <LineChart data={mock_data}/>
    <BarChart data={mock_data}/>
</Grid>

```html
<Grid columns=2>
    <LineChart data={mock_data}/>
    <BarChart data={mock_data}/>
</Grid>
```