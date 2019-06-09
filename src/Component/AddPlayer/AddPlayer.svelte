<script>
  import uuid from "uuid";
  import { createEventDispatcher } from "svelte";

  // This is used to emit event outside the component
  const dispatch = createEventDispatcher();

  // Initial state
  let player = {
    id: uuid(),
    name: "",
    points: 0
  };

  // Dispatch an event for on submit
  const onSubmit = e => {
    e.preventDefault();
    dispatch("addPlayer", player);
    player = {
      id: uuid(),
      name: "",
      points: 0
    };
  };
</script>

<form class="grid-3" on:submit={onSubmit}>
  <input type="text" placeholder="Player Name" bind:value={player.name} />
  <input type="number" placeholder="Player Points" bind:value={player.points} />
  <input type="submit" value="Add Player" class="btn btn-primary" />
</form>
