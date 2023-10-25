<script context="module">
    export const evidenceInclude = true;
</script>

<script>
    import { DataTable } from '@evidence-dev/core-components';
    import { Column } from '@evidence-dev/core-components';
    import { BarChart } from '@evidence-dev/core-components';
	  import formatTitle from '@evidence-dev/component-utilities/formatTitle';
  	import {fmt} from '@evidence-dev/component-utilities/formatting';
    
    export let data;
    export let value;
    export let otherThreshold = 0.03;

    function getColumnNamesWithoutValue(arr, valueColumn) {
  // Get the keys of the first object in the array
  const keys = Object.keys(arr[0]);

  // Filter out the value column from the keys
  const columnNames = keys.filter(column => column !== valueColumn);

  return columnNames;
}

function generateSumDataset(arr, valueColumn) {
  // Get the column names excluding the value column
  const columnNames = getColumnNamesWithoutValue(arr, valueColumn);

  // Create an empty array for the dataset
  const dataset = [];

  // Loop through the column names
  for (let i = 0; i < columnNames.length; i++) {
    const columnName = columnNames[i];
    const columnData = [];

    // Group the sum of the value column by the current column
    let totalValue = 0;
    for (let j = 0; j < arr.length; j++) {
      const row = arr[j];
      const key = row[columnName];
      const value = row[valueColumn];

      if (!columnData.some(obj => obj[columnName] === key)) {
        columnData.push({ column: columnName, [columnName]: key, [valueColumn]: 0 });
      }

      const obj = columnData.find(obj => obj[columnName] === key);
      obj[valueColumn] += value;
      totalValue += value;
    }

    // Calculate the percentage of the total for each row as a decimal number
    for (let j = 0; j < columnData.length; j++) {
      const obj = columnData[j];
      const percentage = obj[valueColumn] / totalValue;
      obj['pct_total_pct1'] = parseFloat(percentage.toFixed(4));
    }

    // Sort the columnData array in descending order based on the value of 'valueColumn'
    columnData.sort((a, b) => b[valueColumn] - a[valueColumn]);

    // Add the column data to the dataset array
    dataset.push(columnData);
  }

  return dataset;
}

let summarizedData = generateSumDataset(data, value)

function aggregateBelowThreshold(sumDataset, valueColumn, otherThreshold) {
  // Loop through each dataset
  for (let i = 0; i < sumDataset.length; i++) {
    const dataset = sumDataset[i];
    let otherItem = null;
    let otherValue = 0;

    // Loop through each item in the dataset
    for (let j = 0; j < dataset.length; j++) {
      const item = dataset[j];
      const pct = item['pct_total_pct1'];

      // Check if the percentage is below the threshold
      if (pct < otherThreshold) {
        // Aggregate the value to the "Other" item
        if (!otherItem) {
          otherItem = { ...item };
          otherItem[otherItem.column] = 'Other';
          otherValue += item[valueColumn];
        } else {
          otherValue += item[valueColumn];
        }

        // Remove the item from the dataset
        dataset.splice(j, 1);
        j--;
      }
    }

    // Add the "Other" item if it exists
    if (otherItem) {
      otherItem[valueColumn] = otherValue;
      dataset.push(otherItem);
    }
  }

  return sumDataset;
}

function hasValuesBelowThreshold(dataset, otherThreshold) {
  for (let i = 0; i < dataset.length; i++) {
    const item = dataset[i];
    const pct = item['pct_total_pct'];

    if (pct < otherThreshold) {
      return true;
    }
  }

  return false;
}

aggregateBelowThreshold(summarizedData, value, otherThreshold)

</script>

<h2 class="markdown">{formatTitle(value)} Breakdown</h2>

{#each summarizedData as column}


<h3 class="markdown">{formatTitle(column[0].column)}</h3>

<BarChart data={column} x={column[0].column} y={value} swapXY=true/>


<p class="markdown text-sm ml-5">"Other" includes any categories below {fmt(otherThreshold, 'pct')} of total {formatTitle(value)}, including x, y, z, and 14 more categories.</p>

<DataTable data={column}>
    <Column id={column[0].column}/>
    <Column id={value}/>
    <Column id=pct_total_pct1/>
</DataTable>

{/each}