<script>
  export let currentEmoji;
  let current = 1;
</script>

<div>
  <div>{currentEmoji}</div>
  <button
    class="btn"
    class:btn-primary={current === 1}
    on:click={() => (current = 1)}
  >
    Button 1
  </button>
  <button
    class="btn"
    class:btn-primary={current === 2}
    on:click={() => (current = 2)}
  >
    Button 2
  </button>
  <button
    class="btn"
    class:btn-primary={current === 3}
    on:click={() => (current = 3)}
  >
    Button 3
  </button>
</div>

<style>
  div {
    font-size: 3em;
    margin-bottom: 0.5em;
  }
</style>
