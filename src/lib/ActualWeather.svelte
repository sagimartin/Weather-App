<script lang="ts">
  export let weatherData: any;
</script>

<div class="actual-weather">
  <img src={weatherData.image} alt="Weather icon" />
  <p class="temperature">{weatherData.temperature}</p>
  <p class="description">{weatherData.description}</p>
</div>

<div class="weather-infos">
  <div class="infos">
    <div class="wind info">
      <span class="material-symbols-outlined"> air </span>
      <div class="text">
        <span>{weatherData.windSpeed}</span>
        <p>Wind speed</p>
      </div>
    </div>

    <div class="feels-like info">
      <span class="material-symbols-outlined"> thermostat </span>
      <div class="text">
        <span>{weatherData.feelsLike}</span>
        <p>Feels like</p>
      </div>
    </div>
  </div>

  <div class="infos">
    <div class="humidity info">
      <span class="material-symbols-outlined"> water </span>
      <div class="text">
        <span>{weatherData.humidity}</span>
        <p>Humidity</p>
      </div>
    </div>
    <div class="pressure info">
      <span class="material-symbols-outlined"> compress </span>
      <div class="text">
        <span>{weatherData.pressure}</span>
        <p>Pressure</p>
      </div>
    </div>
  </div>
</div>

<style>
  .actual-weather img {
    width: 10rem;
  }
</style>
