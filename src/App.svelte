<script>
  import Navbar from './Navbar.svelte'
  import Player from './Player.svelte'
  import AddPlayer from './AddPlayer.svelte'

  let players = [
    {
      name: 'Ash Ketchum',
      points: 0
    },
    {
      name: 'Misty Yawa',
      points: 0
    },
    {
      name: 'Brock',
      points: 0
    }
  ];

  const addPlayer = (e) => {
    const newPlayer = e.detail;
    players = [...players, newPlayer];
  };

  const removePlayer = (e) => {
    // const expiredPlayer = e.detail;
    const expiredPlayer =     {
      name: 'Brock',
      points: 0
    }
    players = players.filter(player => 
      player.name !== expiredPlayer.name
    )
  };
</script>

<Navbar />
<div class="container">
<AddPlayer on:addplayer={addPlayer}/>
<button on:click={removePlayer}>REMOVE BROCK</button>
  {#if players.length === 0}
    <p>No Players</p>
  {:else}
    {#each players as player}
      <Player name={player.name} bind:points={player.points} />
    {/each}
  {/if}
</div>
