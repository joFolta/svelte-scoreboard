<script>
  import Navbar from './Navbar.svelte'
  import Player from './Player.svelte'

  let players = [
    {
      name: 'Ash Ketchum',
      points: 100
    },
    {
      name: 'Misty Yawa',
      points: 100
    },
    {
      name: 'Brock',
      points: 100
    }
  ];
</script>

<Navbar />
<div class="container">
  {#if players.length === 0}
    <p>No Players</p>
  {:else}
    {#each players as player}
      <Player name={player.name} points={player.points} />
    {/each}
  {/if}
</div>
