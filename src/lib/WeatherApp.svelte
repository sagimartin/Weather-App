<script lang="ts">
  import SearchBar from "./SearchBar.svelte";
  import NotFound from "./NotFound.svelte";
  import ActualWeather from "./ActualWeather.svelte";

  let city = "";
  let weatherData: any = {};
  let searchCompleted = false;

  const searchWeather = async () => {
    const APIKey = import.meta.env.VITE_WEATHER_API_KEY;

    if (city === "") return;

    try {
      const response = await fetch(
        `https://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&appid=${APIKey}`
      );
      const json = await response.json();

      if (json.cod === "404") {
        weatherData = {};
      } else {
        weatherData = {
          image: getWeatherImage(json.weather[0].main),
          temperature: `${parseInt(json.main.temp)}°C`,
          description: json.weather[0].description,
          windSpeed: `${parseInt(json.wind.speed)}Km/h`,
          feelsLike: `${parseInt(json.main.feels_like)}°C`,
          pressure: `${parseInt(json.main.pressure)} hPa`,
          humidity: `${json.main.humidity}%`,
        };
      }
    } catch (error) {
      console.error("Error fetching weather data:", error);
    } finally {
      searchCompleted = true;
    }
  };

  const getWeatherImage = (weatherType: string) => {
    switch (weatherType) {
      case "Clear":
        return "sunny.svg";
      case "Rain":
        return "rainy.svg";
      case "Snow":
        return "snowy.svg";
      case "Clouds":
        return "cloudy-sunny.svg";
      case "Wind":
        return "windy.svg";
      case "Thunderstorm":
        return "thunderstorm.svg";
      case "Drizzle":
        return "drizzle.svg";
      case "Haze":
      case "Mist":
      case "Fog":
        return "clouds.svg";
      default:
        return "";
    }
  };

  $: if (city !== "") {
    searchCompleted = false;
  }
</script>

<div class="weather-app">
  <SearchBar bind:city onSearch={searchWeather} />

  {#if city !== "" && searchCompleted}
    {#if Object.keys(weatherData).length > 0}
      <ActualWeather {weatherData} />
    {:else}
      <NotFound />
    {/if}
  {/if}
</div>

<style>
  .weather-app {
    max-height: 90dvh;
    overflow: hidden;
    background-color: white;
    padding: 1rem;
    border-radius: 0.5rem;
    cursor: default;
  }

  @media only screen and (min-device-width: 768px) {
    .weather-app {
      transform: scale(3);
    }
  }
</style>
