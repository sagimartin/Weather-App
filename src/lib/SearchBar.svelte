<script lang="ts">
  import { onMount } from "svelte";

  export let city: string;
  export let onSearch: () => void;

  const handleKeyDown = (event: KeyboardEvent) => {
    if (event.key === "Enter") {
      onSearch();
    }
  };

  const detectLocation = () => {
    navigator.geolocation.getCurrentPosition(async (position) => {
      const { latitude, longitude } = position.coords;
      const APIKey = import.meta.env.VITE_WEATHER_API_KEY;
      try {
        const response = await fetch(
          `https://api.openweathermap.org/data/2.5/weather?lat=${latitude}&lon=${longitude}&appid=${APIKey}`
        );
        const data = await response.json();
        city = data.name || "Unknown City";

        onSearch();
      } catch (error) {
        console.error("Error during location detection:", error.message);
      }
    });
  };

  onMount(() => {
    detectLocation();
  });
</script>

<div class="search-bar">
  <button on:click={detectLocation} class="material-symbols-outlined location">
    my_location
  </button>
  <input
    type="text"
    bind:value={city}
    placeholder="Find a location"
    on:keydown={handleKeyDown}
  />
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
    gap: 0.5rem;
  }

  input {
    width: 13rem;
    border: none;
    text-transform: capitalize;
    font-weight: 600;
    caret-color: transparent;
  }

  input::placeholder {
    text-align: left;
  }

  button {
    background: none;
    border: none;
    cursor: pointer;
    transition: 0.4s ease;
  }

  .location {
    color: rgb(24, 139, 101);
  }

  .location:hover {
    color: black;
  }

  .search {
    color: blueviolet;
  }

  .search:hover {
    color: rgb(89, 0, 255);
  }
</style>
