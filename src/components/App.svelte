<script>
  import Characters from "./Characters.svelte";
  import { onMount } from "svelte";

  const API = "https://rickandmortyapi.com/api/character";
  let query = "";
  let data = [];
  let characters = [];

  onMount(async () => {
    const res = await fetch(API);
    data = await res.json();
    characters = data.results;
  });

  async function onChangeInput() {
    const APIFILTER = `https://rickandmortyapi.com/api/character/?name=${query}`;
    const res = await fetch(APIFILTER);
    data = await res.json();
    characters = data.results;
  }
</script>

<style>
  .search-c {
    width: -moz-available;
    width: -webkit-fill-available;
    width: fill-available;
    margin: 10px;
    font-size: 20px;
    margin-left: 10%;
    margin-right: 10%;
  }
  h1 {
    text-align: center;
  }
</style>

<div class="wrapper">
  <h1>Rick and Morty</h1>
  <label class="search-c">Character:</label>
  <input
    class="search-c"
    type="text"
    name="search"
    bind:value={query}
    on:keydown={onChangeInput} />
  <Characters {characters} />
</div>
