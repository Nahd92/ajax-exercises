<template>
  <div class="weather">
    <h1>Check todays sunset and sunrise</h1>
    <div class="weather-container">
      <h3>Gothenburgs coordinatees:</h3>
      <p>Langitude: 57.708870</p>
      <p>Longitude: 11.974560</p>

      <label>Type in longitude:</label>
      <input type="text" v-model="longitude" placeholder="Longitude" />
      <label>Type in latitude:</label>
      <input type="text" v-model="latitude" placeholder="Latitude" />
      <div class="button">
        <button type="submit" @click="sendWeatherRequest(longitude, latitude)">
          Send Requests
        </button>
      </div>

      <h3 class="weather-title">Today Sun goes up: {{ sunrise }}</h3>
      <h3 class="weather-title">Today Sun goes down: {{ sunset }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: "todaysWeather",
  data: () => ({
    latitude: "",
    longitude: "",
    sunrise: "",
    sunset: "",
  }),
  methods: {
    sendWeatherRequest(longitude, latitude) {
      const url =
        "https://api.sunrise-sunset.org/json?lat=" +
        latitude +
        "&lng=" +
        longitude +
        "&date=today";
      fetch(url)
        .then((request) => request.json())
        .then((data) => {
          this.sunrise = data.results.sunrise;
          this.sunset = data.results.sunset;
        });
    },
  },
};
</script>

<style lang="css" scoped>
h1 {
  text-align: center;
}
.weather-container {
  display: flex;
  justify-items: center;
  flex-direction: column;
}

input[type="text"] {
  margin: 1em 0;
  width: 25%;
}
.button {
  margin: 1em;
}
.weather-title {
  font-size: 2.5em;
}
</style>