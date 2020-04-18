<script>
  // Declaring the props received from parent here. See https://svelte.dev/examples#declaring-props
  export let name;
  export let points;

  let showControls = false;

  // not actually changing App's player.points (just @ display level, ie. Player's points) - this causes the issue where adding a player resets the updated points of current players
  // FIXED: <Player bind:points={} ....> 
  // https://dev.to/joshnuss/managing-state-in-svelte-29o7#data-binding or https://svelte.dev/tutorial/component-bindings  
  const addPoint = () => points += 1;
  const removePoint = () => points -=1;
  const toggleControls = () => showControls = !showControls;
</script>

<style>
	h1 {
		color: #204f6e;
  }
  
  h3 {
    margin-bottom: 10px;
  }
</style>

  <div class="card">
    <h1>
      {name}
      <button class="btn btn-sm" on:click={toggleControls}>
      {#if !showControls}+{:else}-{/if}
      </button>
    </h1>
    <h3>Points: {points}</h3>
    {#if showControls}
      <button class="btn" on:click={addPoint}>+1</button>
      <button class="btn btn-dark" on:click={removePoint}>-1</button>
      <input type="number" bind:value={points}>
    {/if}
  </div>
