<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  export let id;
  export let name;
  export let points;
  let showControls = false;

  const addPoint = () => (points += 1);
  const removePoint = () => (points -= 1);
  const toggleControls = () => (showControls = !showControls);

  const deletePlayer = () => dispatch("removePlayer", id);
</script>

<style>
  h1 {
    color: #204f5e;
  }
</style>

<div class="container">
  <div class="card">
    <h1 data-id={id}>
       {name}
      <button class="btn btn-sm" on:click={toggleControls}>
        {#if showControls}-{:else}+{/if}
      </button>
      <button class="btn btn-danger btn-sm" on:click={deletePlayer}>x</button>
    </h1>
    <h3>Points: {points}</h3>
    {#if showControls}
      <button class="btn" on:click={addPoint}>+1</button>
      <button class="btn btn-dark" on:click={removePoint}>-1</button>
      <input type="number" bind:value={points} />
    {/if}
  </div>
</div>
