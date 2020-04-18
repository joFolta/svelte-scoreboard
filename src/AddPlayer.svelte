<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  let player = {
    name: '',
    points: 0
  };
  let unNamedPlayerCount = 0;
  const unNamedPlayerNamer = () => {
    if (player.name === ''){
      unNamedPlayerCount += 1;
      player.name = `Player ${unNamedPlayerCount}`;
    };
  };

  const onSubmit = (e) => {
    e.preventDefault();
    unNamedPlayerNamer();
    dispatch("addplayer", player);
    // Reset form
    player = {
      name: '',
      points: 0
    };
  };

</script>

<form on:submit={onSubmit} class="grid-3">
  <input type="text" placeholder="Player Name" bind:value={player.name}>
  <input type="number" placeholder="Player Points" bind:value={player.points}>
  <input type="submit" class="btn btn-primary" value="Add Player">
</form>