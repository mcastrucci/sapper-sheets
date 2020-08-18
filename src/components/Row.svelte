<script>
  export let row;
  export let cols;
  export let rowData;
  export let handleChangedCell

  import Cell from "./Cell.svelte";
</script>

<style>
  .row {
    display: block;
  }
</style>

<div class="row">
  {#each Array(cols) as _, col}
    <Cell
      {row}
      {col}
      value={rowData[col] || ''}
      onChangedValue={handleChangedCell} />
  {/each}
</div>
