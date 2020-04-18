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

// upgrade so you can type in their name
// upgrade so you can type in their name
// upgrade so you can type in their name
  const removeBrock = (e) => {
    // const expiredPlayer = e.detail;
    const expiredPlayer = {
      name: 'Brock',
      points: 0
    };
    players = players.filter(player => 
      player.name !== expiredPlayer.name
    );
  };
  const removePlayer = (e) => {
    const removePlayerName = e.detail;
    players = players.filter(player => 
      player.name !== removePlayerName
    );
  };
</script>

<Navbar />
<div class="container">
<AddPlayer on:addplayer={addPlayer}/>
<button class="btn btn-primary" on:click={removeBrock}>REMOVE BROCK</button>
  {#if players.length === 0}
    <p>No Players</p>
  {:else}
    {#each players as player}
      <Player 
        name={player.name} 
        bind:points={player.points} 
        on:removeplayer={removePlayer}
      />
    {/each}
  {/if}
</div>
