<script>
  import Row from "./Row.svelte";

  let cols = 8;
  let rows = 15;
  export let tableIdentifier;

  let data = {};

  const handleChangedCell = (col, row, value) => {
    if (!data[row]) data[row] = {};
    data[row][col] = value;

    if (window && window.localStorage) {
      window.localStorage.setItem(tableIdentifier, JSON.stringify(data));
    }
  };

  onMount(() => {
    if (typeof window !== "undefined") {
      const localStorageData = window.localStorage.getItem(tableIdentifier);
      if (localStorageData) {
        data = JSON.parse(localStorageData);
      }
    }
  });

  import { onMount } from "svelte";
</script>

{#each Array(rows) as _, row}
  <Row {row} {cols} rowData={data[row] || {}} {handleChangedCell} />
{/each}
