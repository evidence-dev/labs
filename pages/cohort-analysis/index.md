<script>
    // Due to the location that Evidence builds the site, we need to hop up many directories to get to root
    import CohortAnalysis from "../../../../../src/lib/charts/analysis/CohortAnalysis.svelte";
</script>

# Cohort Analysis

```cohorts
select '2023-01-01' as cohort, 0 as period, 8347 as metric
union all
select '2023-01-01' as cohort, 1 as period, 7499 as metric
union all
select '2023-01-01' as cohort, 2 as period, 4477 as metric
union all
select '2023-01-01' as cohort, 3 as period, 2474 as metric
union all
select '2023-01-01' as cohort, 4 as period, 1244 as metric
union all
select '2023-01-01' as cohort, 5 as period, 944 as metric

union all

select '2023-01-02' as cohort, 0 as period, 2399 as metric
union all
select '2023-01-02' as cohort, 1 as period, 877 as metric
union all
select '2023-01-02' as cohort, 2 as period, 839 as metric
union all
select '2023-01-02' as cohort, 3 as period, 654 as metric
union all
select '2023-01-02' as cohort, 4 as period, 338 as metric

union all

select '2023-01-03' as cohort, 0 as period, 848 as metric
union all
select '2023-01-03' as cohort, 1 as period, 766 as metric
union all
select '2023-01-03' as cohort, 2 as period, 544 as metric
union all
select '2023-01-03' as cohort, 3 as period, 234 as metric
union all
select '2023-01-03' as cohort, 4 as period, 134 as metric
```

This is an experimental component, with issues still to be solved.
- Incomplete periods are currently not removed from calculations or shown as blanks. This may require either an assumption of time grain, or that the dataset exclude any incomplete time periods.
- Number formatting should be an option
- Component should allow for differently named columns than `cohort`, `period`, and `metric`
- Data structure requried for this component may change
- Component does not contain any error handling

<CohortAnalysis data={cohorts} periodLength=day/>