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
      <div class="data">
        <span class="material-symbols-outlined"> air </span>
        <span>{weatherData.windSpeed}</span>
      </div>
      <p>Wind speed</p>
    </div>

    <div class="humidity info">
      <div class="data">
        <span class="material-symbols-outlined"> water </span>
        <span>{weatherData.humidity}</span>
      </div>
      <p>Humidity</p>
    </div>
  </div>

  <div class="infos">
    <div class="pressure info">
      <div class="data">
        <span class="material-symbols-outlined"> compress </span>
        <span>{weatherData.pressure}</span>
      </div>
      <p>Air pressure</p>
    </div>

    <div class="feels-like info">
      <div class="data">
        <span class="material-symbols-outlined"> thermostat </span>
        <span>{weatherData.feelsLike}</span>
      </div>
      <p>Feels like</p>
    </div>
  </div>
</div>

<style>
  .actual-weather {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 2rem;
  }

  .actual-weather img {
    width: 10rem;
    max-width: 50dvw;
    margin: 1rem 0;
  }

  .temperature {
    font-size: 2rem;
  }

  .description {
    font-size: 1.5rem;
    font-weight: 600;
    color: rgba(0, 0, 255, 0.59);
  }

  .weather-infos {
    margin: 0 0.5rem;
    display: flex;
    justify-content: space-between;
  }

  .infos {
    display: flex;
    flex-direction: column;
    font-size: 1rem;
    gap: 1rem;
  }

  .data {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    gap: 0.1rem;
    font-size: 1rem;
    font-weight: 600;
  }

  .info > p {
    font-weight: 600;
    color: rgb(175, 171, 237);
  }
</style>
