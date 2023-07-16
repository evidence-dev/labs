<script>
    // Due to the location that Evidence builds the site, we need to hop up many directories to get to root
    import Grid from "../../../../../src/lib/ui/Grid.svelte";
    import Group from "../../../../../src/lib/ui/Group.svelte";
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

# Group Component

The Group component lets you include multiple items inside a grid cell. This is helpful if you want to include markdown along with a chart, for example.

One note is that the markdown requires specific line spacing to work correctly, which can be unintuitive. Generally it requires a blank line before and after a markdown item.

## Section 3
<Grid columns=3>
    <Group>

        ### Line
        This is a line chart

        <LineChart data={mock_data}/>
    </Group>

    <Group>

        ### Bar
        This is a bar chart

        <BarChart data={mock_data}/>
    </Group>

    <Group>

        ### Area
        This is an area chart

        <AreaChart data={mock_data}/>
    </Group>
</Grid>

```html
<Grid columns=3>
    <Group>

        ### Line
        This is a line chart

        <LineChart data={mock_data}/>
    </Group>

    <Group>

        ### Bar
        This is a bar chart

        <BarChart data={mock_data}/>
    </Group>

    <Group>

        ### Area
        This is an area chart

        <AreaChart data={mock_data}/>
    </Group>
</Grid>
```