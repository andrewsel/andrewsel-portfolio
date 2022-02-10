<script>
  export let filter;
  export let index;
  export let toggleFilter;
</script>

<div class={filter[1] ? "active" : ""} on:click={toggleFilter(index)}>
  {filter[0]}
</div>

<style>
  div {
    padding: 3px 12px;
    border: 1px solid black;
    border-radius: 100px;
    margin: 0 4px;
    font-size: var(--font-sm);
    cursor: pointer;
    user-select: none;
  }

  .active {
    background-color: black;
    color: white;
  }
</style>
