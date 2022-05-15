<script>
  import { fade, fly } from "svelte/transition";
  import EmojiDisplay from "./EmojiDisplay.svelte";
  import EmojiDescription from "./EmojiDescription.svelte";
  import Button from "./Button.svelte";

  let isLoaded = false;
  let currentEmoji = "😍";
  const emojis = ["😁", "🤪", "🤩", "👹", "🥶", "😍"];

  function randomizeEmoji() {
    return emojis[Math.floor(Math.random() * emojis.length)];
  }
  function handleRandomButton() {
    currentEmoji = randomizeEmoji();
  }
  setTimeout(() => {
    isLoaded = true;
  }, 2000);
</script>

<svelte:head>
  <link rel="stylesheet" href="/style.css" />
  <link rel="stylesheet" href="/terminal.css" />
</svelte:head>

<div class="container">
  <h1>Randomize Emoji</h1>
  <ul>
    {#each emojis as emoji}
      <li>{emoji}</li>
    {/each}
  </ul>
  {#if isLoaded === true}
    <div in:fly={{ y: 200, duration: 2000 }} out:fade>
      <EmojiDisplay {currentEmoji} />
      <EmojiDescription />
      <Button on:click={handleRandomButton} title="🔁 Randomize" />
    </div>
  {:else}
    <h2>Loading...</h2>
  {/if}
  <Button title={"Toggle"} on:click={() => (isLoaded = !isLoaded)} />
</div>

<style>
  div {
    margin: 2em;
  }
  ul {
    margin-bottom: 6em;
  }
</style>
