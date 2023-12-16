<script lang="ts">
  export let city: string;
  export let onSearch: () => void;
</script>

<div class="search-bar">
  <span class="material-symbols-outlined"> location_on </span>
  <input type="text" bind:value={city} placeholder="Find a location" />
  <button
    on:click={onSearch}
    class="material-symbols-outlined search"
    aria-label="Search"
  >
    search
  </button>
</div>

<style>
  .search-bar {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
  }

  .search-bar > input {
    padding: 0.2rem;
    border: none;
    text-transform: uppercase;
    font-weight: 600;
    caret-color: transparent;
  }

  button {
    color: black;
    background-color: rgb(175, 171, 237);
    border-radius: 50%;
    border: none;
    padding: 0.2rem;
    cursor: pointer;
    scale: 0.8;
    transition: 0.4s ease;
  }

  button:hover {
    color: rgb(89, 0, 255);
    scale: 0.9;
  }
</style>
