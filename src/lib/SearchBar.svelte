<script lang="ts">
    export let city: string;
    export let onSearch: () => void;
  </script>
  
  <div class="search-bar">
    <input type="text" bind:value={city} placeholder="Find a location" />
    <button on:click={onSearch} class="material-symbols-outlined search" aria-label="Search">
        search
    </button>
  </div>
  
  <style>
  </style>
  