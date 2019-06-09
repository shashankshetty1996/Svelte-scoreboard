<script>
  import uuid from "uuid";

  import Navbar from "./component/Navbar/Navbar.svelte";
  import Player from "./component/Player/Player.svelte";
  import AddPlayer from "./component/AddPlayer/AddPlayer.svelte";

  let players = [
    {
      id: uuid(),
      name: "Shashank",
      points: 42
    },
    {
      id: uuid(),
      name: "Nilesh",
      points: 36
    },
    {
      id: uuid(),
      name: "Keerthi",
      points: 34
    },
    {
      id: uuid(),
      name: "Prashant",
      points: 52
    }
  ];

  // Add a player
  const addPlayer = e => {
    // e.detail will give all the data emited from component's event.
    const newPlayer = e.detail;

    players = [...players, newPlayer];
  };

  // Remove a player
  const removePlayer = e => {
    const playerID = e.detail;

    players = players.filter(player => player.id !== playerID);
  };
</script>

<Navbar />
<div class="container">
  <AddPlayer on:addPlayer={addPlayer} />
  {#if players.length === 0}
    <p>No Players</p>
  {:else}
    {#each players as player}
      <Player
        id={player.id}
        name={player.name}
        points={player.points}
        on:removePlayer={removePlayer} />
    {/each}
  {/if}
</div>
