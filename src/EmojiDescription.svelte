<script>
  import { onMount, onDestroy, beforeUpdate, afterUpdate } from "svelte";

  let description = "";
  $: characters = description.length;
  $: words = description.split(" ").length;

  function handleSubmit(event) {
    console.log("form submitted. thanks!");
    description = "";
  }

  // Test lifecycle
  onMount(function () {
    console.log("onMount");
  });
  onDestroy(function () {
    console.log("onDestroy");
  });
  beforeUpdate(function () {
    console.log("beforeUpdate");
  });
  afterUpdate(function () {
    console.log("afterUpdate");
  });
</script>

<div class="form-group">
  <p>{description}</p>
  <form on:submit|preventDefault={handleSubmit}>
    <textarea bind:value={description} rows="7" />
    <button type="submit">Save</button>
  </form>
  <p>Character count: {characters}</p>
  <p>Words count: {words}</p>
</div>

<style>
  div {
    margin-top: 1em;
    margin-bottom: 1em;
  }
</style>
