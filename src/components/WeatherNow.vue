<template>
  <div class="weather-now">
    <div class="weather-now iconWeatherNow">
      <img
        :src="require(`../assets/icons/${determineWeatherIcon(1)}.png`)"
        id="weather weatherNowIcon"
      />
    </div>
    <div class="weather-now temp-now">
      {{ weatherData[0]["data"]["instant"]["details"]["air_temperature"] }}°
    </div>
    <div class="weather-now detailsWeatherNow">
      <div class="weather-now detailsWeatherNow percipitation">
        Regn:
        {{
          weatherData[0]["data"]["next_1_hours"]["details"][
            "precipitation_amount"
          ]
        }} mm
      </div>
      <div class="weather-now detailsWeatherNow humidity">
        Fuktighet:
        {{ weatherData[0]["data"]["instant"]["details"]["relative_humidity"] }}%
      </div>
      <div class="weather-now detailsWeatherNow wind">
        Vind:
        {{ weatherData[0]["data"]["instant"]["details"]["wind_speed"] }} m/s
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "WeatherNow",
  props: {
    weatherData: {
      type: Array,
    },
//   },
//   data() {
//     return {};
  },
  methods: {
    determineWeatherIcon(idx) {
      if (this.weatherData === []) {
        //assigning an arbitrary icon before the weatherData array is populated
        const icon = "cloudy.png";
        return icon;
      }
      const icon = this.weatherData[idx].data.next_12_hours.summary.symbol_code;
      return icon;
    },
  },
};
</script>

<style scoped>

.weather-now {
  min-height: 25%;
  width: 50%;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: space-around;
  align-content: center;
  align-items: center;
}
img {
  /* max-width: 120%;*/
  max-height: 120px;
  display: block; 
  margin: 0 auto;
}
.temp-now {
  order: 0;
  flex: 0 1 auto;
  align-self: auto;
  height: 90%;
  font-size: 70px;
  font-weight: 900;
}
.detailsWeatherNow {
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  justify-content: space-around;
  align-content: stretch;
  align-items: flex-start;
  height: 50%;
  width: 8em;
}
.iconWeatherNow {
  order: 0;
  flex: 1 1 auto;
  align-self: auto;
  height: 50%;
}
.percipitation {
  order: 0;
  flex: 0 1 auto;
  align-self: auto;
  font-size: 12px;
  width: 100%;
}
.humidity {
  order: 0;
  flex: 0 1 auto;
  align-self: auto;
  font-size: 12px;
  width: 100%;
}
.wind {
  order: 0;
  flex: 0 1 auto;
  align-self: auto;
  font-size: 12px;
  width: 100%;
}
</style>
