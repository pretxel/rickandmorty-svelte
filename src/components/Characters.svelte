<script>
  export let characters;
</script>

<style>
  .characters {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-gap: 8px;
  }
  figure,
  img {
    width: 100%;
    margin: 0;
  }
</style>

<div class="characters">
  {#each characters as character}
    <figure>
      <img src={character.image} alt={character.name} />
      <figcaption>{character.name}</figcaption>
    </figure>
  {:else}
    <p>loading...</p>
  {/each}
</div>
