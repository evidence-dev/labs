<script>
    // Due to the location that Evidence builds the site, we need to hop up many directories to get to root
    import Summarizer from "../../../../../src/lib/charts/analysis/Summarizer.svelte";
</script>

# Summarizer

<Alert status=warning>
This component requires the `formatTitle` and `formatValue` functions found in the `@evidence-dev/component-utilities` package. These are currently excluded from the component and as a result, some titles and values will be unformatted.
</Alert>

This component is a proof of concept for "analysis components" - components you can give a dataset to with minimal details, and have them complete aggregations and summaries for you.

```sql categories
select 'A' as category, 'West' as region, 120 as sales_usd
union all
select 'B' as category, 'East' as region, 2420 as sales_usd
union all
select 'C' as category, 'West' as region, 6443 as sales_usd
union all
select 'D' as category, 'East' as region, 5354 as sales_usd
union all
select 'E' as category, 'West' as region, 8459 as sales_usd
```

<Summarizer data={categories} value=sales_usd/>