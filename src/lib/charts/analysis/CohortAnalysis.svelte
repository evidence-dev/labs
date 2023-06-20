<script context="module">
    export const evidenceInclude = true;
</script>

<script>
    import { formatValue } from '@evidence-dev/component-utilities/formatting';
    // import DownloadData from '$lib/ui/DownloadData.svelte'
    export let data;
    
    let hovering=true
    
    export let periodLength = 'week'; // day, week, month
    
        let daymap = {
            day: 1,
            week: 7,
            month: 30,
            quarter: 90,
            year: 365
        }
    
        // accepts data with columns:
        // 1. Cohort (date)
        // 2. Age (integer)
        // 3. Metric (e.g., count, MRR, etc.)
    
        function processDataset(dataset) {
            // Sort the dataset by cohort ascending and period ascending
            dataset.sort((a, b) => {
                if (a.cohort === b.cohort) {
                return a.period - b.period;
                }
                return new Date(a.cohort) - new Date(b.cohort);
            });
    
            // Find the minimum metric value for each cohort based on period
            const minMetrics = {};
            for (const data of dataset) {
                if (!minMetrics[data.cohort] || data.period < minMetrics[data.cohort].period) {
                minMetrics[data.cohort] = data;
                }
            }
    
            // Add the additional column with metric divided by the minimum metric for each cohort
            const processedDataset = dataset.map((data) => ({
                ...data,
                metricRatio: data.metric / minMetrics[data.cohort].metric,
            }));
    
            return processedDataset;
        }
    
        let cohortData = processDataset(data);
    
        function getDistinctValues(data, column) {
            let distinctValues = [];
            const distinctValueSet = new Set();
            data.forEach(d => {
            distinctValueSet.add(d[column]);
            });
            distinctValues = [...distinctValueSet];
            return distinctValues;
        }
    
        let cohortList = getDistinctValues(cohortData, 'cohort')
        let maxPeriod = Math.max(...getDistinctValues(cohortData, 'period'))
    
        function generateArray(num) {
            var arr = [];
            for (var i = 1; i <= num; i++) {
                arr.push(i);
            }
            return arr;
        }
    
        let periodList = generateArray(maxPeriod)
    
        function addDays(date, days) {
            var result = new Date(date);
            result.setDate(result.getDate() + days);
            return result;
        }
    
        function calculateTotalByPeriod(data) {
            const totalByPeriod = {};
            const totalCohort = 'Total';
    
            // Calculate metric sum for each period
            for (const row of data) {
                const { period, metric } = row;
                if (!totalByPeriod[period]) {
                totalByPeriod[period] = { cohort: totalCohort, period, metric: 0 };
                }
                totalByPeriod[period].metric += metric;
            }

            // Find the minimum metric for the total cohort
            const minPeriod = Math.min(...Object.keys(totalByPeriod));

            // Calculate metricRatio for each row
            for (const row of Object.values(totalByPeriod)) {
                row.metricRatio = row.metric / totalByPeriod[minPeriod].metric;
            }

            return Object.values(totalByPeriod);
        }
    
    
        let totalData = calculateTotalByPeriod(cohortData)
    
    
        let valueType = 'metricRatio'
    </script>
    
    <select id=valueType bind:value={valueType} class=toggle>
        <option value=metricRatio>Percentage</option>
        <option value=metric>Value</option>
    </select>
    
    <div class=table-container>
    <table>
        <thead>
            <tr>
                <th>Cohort</th>
                <th>Size</th>
                {#each periodList as period}
                    <th>{period}</th>
                {/each}
            </tr>
        </thead>
        <tbody>
        {#each cohortList as cohort}
            <tr>
                <td>{cohort}</td>
                <td>{formatValue(cohortData.filter(d => d.cohort === cohort && d.period === 0)[0]?.metric ?? '', {formatCode: '#,##0', valueType: 'number'})}</td>
                {#each periodList as period}
                    {#if valueType === 'metricRatio'}
                    <td
                        style="background-color: hsla(127, 100%, 26%, {cohortData.filter(d => d.cohort === cohort && d.period === period)[0]?.metricRatio})"
                    >{cohortData.filter(d => d.cohort === cohort && d.period === period)[0]?.[valueType].toLocaleString(undefined, {style: 'percent', minimumFractionDigits:1}) ?? (addDays(cohort, period * daymap[periodLength]) <= new Date() ? '0.0%' : '')}</td>
                    {:else}
                    <td
                        style="background-color: hsla(127, 100%, 26%, {cohortData.filter(d => d.cohort === cohort && d.period === period)[0]?.metricRatio ?? (addDays(cohort, period * daymap[periodLength]) <= new Date() ? '0' : '')})"
                    >{formatValue(cohortData.filter(d => d.cohort === cohort && d.period === period)[0]?.[valueType] ?? '', {formatCode: '#,##0', valueType: 'number'})}</td>
                    {/if}
                {/each}
            </tr>
    
        {/each}
        </tbody>
    </table>
    
    <table>
        <tbody>
            <tr style="border-top: 1px solid lightgrey;">
                <td>Total</td>
                <td>{totalData.filter(d => d.period === 0)[0]?.metric.toLocaleString() ?? ''}</td>
                {#each periodList as period}
                    {#if valueType === 'metricRatio'}
                    <td
                        style="background-color: hsla(127, 100%, 26%, {totalData.filter(d => d.period === period)[0]?.metricRatio})"
                    >{totalData.filter(d => d.period === period)[0]?.[valueType].toLocaleString(undefined, {style: 'percent', minimumFractionDigits:1}) ?? ''}</td>
                    {:else}
                    <td
                        style="background-color: hsla(127, 100%, 26%, {totalData.filter(d => d.period === period)[0]?.metricRatio ?? ''})"
                    >{totalData.filter(d => d.period === period)[0]?.[valueType] ?? ''}</td>
                    {/if}
                {/each}
            </tr>
        </tbody>
    </table>
    </div>
    
    <style>
        .table-container {
            overflow-x: scroll;
            font-family: sans-serif;
            font-size: 9pt;
            max-height: 500px;
        }
    
        td {
            white-space: nowrap;
            min-width: 70px;
            text-align: center;
        }
    
        tr>th:first-child,tr>td:first-child {
            position: sticky;
            left: 0;
            background-color: white;
            min-width: 70px;
        }
    
        tr>th:first-child, tr>th:nth-child(2) {
            z-index: 2;
        }
    
        tr>th:nth-child(2),tr>td:nth-child(2) {
            position: sticky;
            left: 70px;
            background-color: white;
        }
    
        th {
            position: sticky;
            top: 0px;
            background-color: white;
            z-index: 1;
        }

        .toggle {
            font-family: sans-serif;
            font-size: 10pt;
            color: var(--grey-600);
            background-color: var(--grey-100);
            border: 1px solid var(--grey-200);
            padding: 2px 5px;
            border-radius: 5px;
            cursor: pointer;
            margin-bottom: 8px;
        }

        .toggle:focus {
            outline: none;
        }
    
    </style>