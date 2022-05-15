<script>
  let description = "";
  $: characters = description.length;
  $: words = description.split(" ").length;
</script>

<div>
  <p>{description}</p>
  <textarea bind:value={description} rows="7" />
  <p>Character count: {characters}</p>
  <p>Words count: {words}</p>
</div>

<style>
  div {
    margin-top: 1em;
    margin-bottom: 1em;
  }
</style>
