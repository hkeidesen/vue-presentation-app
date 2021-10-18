<template>
  <div class="weather-card">
    <p>
      Værmelding for Sluppen, {{ getDaysAhead(0)["dateNameAhead"] }},
      {{ getDaysAhead()["dateNow"] }}
    </p>
    <div class="weather-now">
      <div class="weather-now iconWeatherNow">
        <img
          id="weather weatherNowIcon"
          :src="require(`../assets/icons/${determineWeatherIcon(1)}.png`)"
        />
      </div>
      <div class="weather-now temp-now">
        {{ weatherData[0]['data']['instant']['details']['air_temperature']}}°
      </div>
      <div class="weather-now detailsWeatherNow">
        <div class="weather-now detailsWeatherNow percipitation">Regn: {{ weatherData[0]['data']['next_1_hours']['details']['precipitation_amount']}} mm</div>
        <div class="weather-now detailsWeatherNow humidity">Fuktighet: {{ weatherData[0]['data']['instant']['details']['relative_humidity']}}%</div>
        <div class="weather-now detailsWeatherNow wind">Vind: {{ weatherData[0]['data']['instant']['details']['wind_speed']}} m/s</div>
      </div>
    </div>
    <div class="temperature-graph">
      <WeatherGraph
        :temperatureDataToPlot="[
          { time: weatherData[0]['time'].slice(11,16), temperature: weatherData[0]['data']['instant']['details']['air_temperature'] },
          { time: weatherData[1]['time'].slice(11,16), temperature: weatherData[1]['data']['instant']['details']['air_temperature'] },
          { time: weatherData[2]['time'].slice(11,16), temperature: weatherData[2]['data']['instant']['details']['air_temperature'] },
          { time: weatherData[3]['time'].slice(11,16), temperature: weatherData[3]['data']['instant']['details']['air_temperature'] },
          { time: weatherData[4]['time'].slice(11,16), temperature: weatherData[4]['data']['instant']['details']['air_temperature'] },
          { time: weatherData[5]['time'].slice(11,16), temperature: weatherData[5]['data']['instant']['details']['air_temperature'] },
          { time: weatherData[6]['time'].slice(11,16), temperature: weatherData[6]['data']['instant']['details']['air_temperature'] },
          { time: weatherData[7]['time'].slice(11,16), temperature: weatherData[7]['data']['instant']['details']['air_temperature'] },
          { time: weatherData[8]['time'].slice(11,16), temperature: weatherData[8]['data']['instant']['details']['air_temperature'] },
          { time: weatherData[9]['time'].slice(11,16), temperature: weatherData[9]['data']['instant']['details']['air_temperature'] },
        ]"
      />
    </div>
    <div class="weather-objects">
      <div class="detailed-weather">
        <p class="day">{{ getDaysAhead(1)["dateNameAhead"].slice(0, 10) }}</p>
        <div class="icon">
          <img
            :src="require(`../assets/icons/${determineWeatherIcon(1)}.png`)"
          />
        </div>
        <div class="temperature">
          <div class="tLow">
            {{
              getHighAndLowTemperatures(
                getDaysAhead(1)["dateAhead"].slice(0, 10)
              )["min_temp"]
            }}°
          </div>
          <div class="tHigh">
            {{
              getHighAndLowTemperatures(
                getDaysAhead(1)["dateAhead"].slice(0, 10)
              )["max_temp"]
            }}°
          </div>
        </div>
      </div>

      <div class="detailed-weather">
        <p class="day">{{ getDaysAhead(2)["dateNameAhead"] }}</p>
        <div class="icon">
          <div class="icon">
            <img
              :src="require(`../assets/icons/${determineWeatherIcon(2)}.png`)"
            />
          </div>
        </div>
        <div class="temperature">
          <div class="tLow">
            {{
              getHighAndLowTemperatures(
                getDaysAhead(2)["dateAhead"].slice(0, 10)
              )["min_temp"]
            }}°
          </div>
          <div class="tHigh">
            {{
              getHighAndLowTemperatures(
                getDaysAhead(2)["dateAhead"].slice(0, 10)
              )["max_temp"]
            }}°
          </div>
        </div>
      </div>

      <div class="detailed-weather">
        <p class="day">{{ getDaysAhead(3)["dateNameAhead"] }}</p>
        <div class="icon">
          <div class="icon">
            <img
              :src="require(`../assets/icons/${determineWeatherIcon(3)}.png`)"
            />
          </div>
        </div>
        <div class="temperature">
          <div class="tLow">
            {{
              getHighAndLowTemperatures(
                getDaysAhead(3)["dateAhead"].slice(0, 10)
              )["min_temp"]
            }}°
          </div>
          <div class="tHigh">
            {{
              getHighAndLowTemperatures(
                getDaysAhead(3)["dateAhead"].slice(0, 10)
              )["max_temp"]
            }}°
          </div>
        </div>
      </div>

      <div class="detailed-weather">
        <p class="day">{{ getDaysAhead(4)["dateNameAhead"] }}</p>
        <div class="icon">
          <div class="icon">
            <img
              :src="require(`../assets/icons/${determineWeatherIcon(4)}.png`)"
            />
          </div>
        </div>
        <div class="temperature">
          <div class="tLow">
            {{
              getHighAndLowTemperatures(
                getDaysAhead(4)["dateAhead"].slice(0, 10)
              )["min_temp"]
            }}°
          </div>
          <div class="tHigh">
            {{
              getHighAndLowTemperatures(
                getDaysAhead(4)["dateAhead"].slice(0, 10)
              )["max_temp"]
            }}°
          </div>
        </div>
      </div>
      <div class="detailed-weather">
        <p class="day">{{ getDaysAhead(5)["dateNameAhead"] }}</p>
        <div class="icon">
          <div class="icon">
            <img
              :src="require(`../assets/icons/${determineWeatherIcon(5)}.png`)"
            />
          </div>
        </div>
        <div class="temperature">
          <div class="tLow">
            {{
              getHighAndLowTemperatures(
                getDaysAhead(5)["dateAhead"].slice(0, 10)
              )["min_temp"]
            }}°
          </div>
          <div class="tHigh">
            {{
              getHighAndLowTemperatures(
                getDaysAhead(5)["dateAhead"].slice(0, 10)
              )["max_temp"]
            }}°
          </div>
        </div>
      </div>
      <div class="detailed-weather">
        <p class="day">{{ getDaysAhead(6)["dateNameAhead"] }}</p>
        <div class="icon">
          <div class="icon">
            <img
              :src="require(`../assets/icons/${determineWeatherIcon(4)}.png`)"
            />
          </div>
        </div>
        <div class="temperature">
          <div class="tLow">
            {{
              getHighAndLowTemperatures(
                getDaysAhead(6)["dateAhead"].slice(0, 10)
              )["min_temp"]
            }}°
          </div>
          <div class="tHigh">
            {{
              getHighAndLowTemperatures(
                getDaysAhead(6)["dateAhead"].slice(0, 10)
              )["max_temp"]
            }}°
          </div>
        </div>
      </div>
      <div class="detailed-weather">
        <p class="day">{{ getDaysAhead(7)["dateNameAhead"] }}</p>
        <div class="icon">
          <div class="icon">
            <img
              :src="require(`../assets/icons/${determineWeatherIcon(7)}.png`)"
            />
          </div>
        </div>
        <div class="temperature">
          <div class="tLow">
            {{
              getHighAndLowTemperatures(
                getDaysAhead(7)["dateAhead"].slice(0, 10)
              )["min_temp"]
            }}°
          </div>
          <div class="tHigh">
            {{
              getHighAndLowTemperatures(
                getDaysAhead(7)["dateAhead"].slice(0, 10)
              )["max_temp"]
            }}°
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import moment from "moment";
import WeatherGraph from "./WeatherGraph";

export default {
  name: "Home",
  components: {
    WeatherGraph,
  },
  data() {
    return {
      weatherData: [],
      timer: "",
    };
  },

  methods: {
    getIndexOfDayOfInterest(day) {
      const indexForWeatherReport = this.weatherData
        .map(function(e) {
          return e.time;
        })
        .indexOf(day);
      console.log("indexForWeatherReport: ", indexForWeatherReport);
      return indexForWeatherReport;
    },
    determineWeatherIcon(idx) {
      //need an error handler here
      const icon = this.weatherData[idx].data.next_12_hours.summary.symbol_code;
      console.log("icon", icon);
      return icon;
    },
    getHighAndLowTemperatures(dateOfInterest) {
      //this function is used to get the max and min temperature for a certain day
      // create an empty array, which is is used to store the indexes of the array for a certain day,
      // i.e.: if the day 2021-09-22 has index 1,2,...,n, the index will be stored here.

      var temp_array = [];
      // uses the weatherData array that is obtained from the met.no-api call
      var arr = this.weatherData;

      // console.log('arr.time '+arr[2]['time'])
      for (var n = 0; n < arr.length; n++) {
        if (arr[n]["time"].slice(0, 10) === dateOfInterest) {
          temp_array.push(
            this.weatherData[n].data.instant.details.air_temperature
          );
        }
      }
      const max_temp = Math.max(...temp_array);
      const min_temp = Math.min(...temp_array);
      // console.log('max_temp', Math.max(...temp_array))
      // console.log('temp', temp_array)
      // console.log('temp_array', temp_array)
      return { max_temp, min_temp, temp_array };
      // console.log('logging weather data', this.weatherData[indices[0]].data.instant.details.air_temperature);
    },

    getDaysAhead(daysAhead) {
      // returns the date of format yyyy-mm-ddThh:mm:ssZ
      const dateNameAhead = moment()
        .add(daysAhead, "days")
        .format("dddd");
      const dateAhead = moment()
        .add(daysAhead, "days")
        .format();
      const dateNow = moment().format("MMM Do");
      return { dateNameAhead, dateAhead, dateNow };
    },
    async fetchWeatherData() {
      const response = await fetch("https://api.met.no/weatherapi/locationforecast/2.0/compact?lat=63.4308&lon=10.4034");
      const data = await response.json();
      if (response.ok) {
        console.log("Data fetched succesfully!");
        console.log('response', data.properties.timeseries)
      }
      return data.properties.timeseries;
    },

  },
  async created() {
    this.weatherData = await this.fetchWeatherData();
    // console.log(this.weatherData[0].data.next_6_hours.details.air_temperature_min)
    moment.locale("nb");
    setInterval(
      async () => (this.weatherData = await this.fetchWeatherData()),
      60*60*1000
    );
  },
};
</script>

<style scoped>
.weather-card {
  position: absolute;
  margin-left: 25px;
  width: 750px;
  height: 500px;
  /* border: solid 2px red; */
  border-radius: 15px;
  display: flex;
  flex-direction: column;
  flex: 1;
}
.weather-now {
  /* border: solid 1px cyan; */
  height: 25%;
  width: 50%;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: space-around;
  align-content: center;
  align-items: center;
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
  height: 80%;
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

.temperature-graph {
  /* border: 1px solid red; */
  order: 0;
  flex: 0 1 auto;
  align-self: auto;
  /* height: 2%; */
  position: flex-end;
  /* border-radius: 10px;
  -webkit-box-shadow: 0px 0px 7px 0px rgba(0, 0, 0, 0.42);
  box-shadow: 0px 0px 7px 0px rgba(0, 0, 0, 0.42); */
}
.weather-objects {
  /* border: 1px solid red; */
  margin-top: 20px;
  border-radius: 15px;
  height: 30%;
  /* width: 725px; */
  flex-direction: row;
  display: flex;
  /* justify-content: stretch; */
  padding: 4px;
  padding-left: 4px;
  padding-right: 4px;
}
.detailed-weather {
  align-items: center;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-flow: column;
  flex: 1;
  border-radius: 10px;
  margin-right: 2px;
  margin-left: 2px;
  -webkit-box-shadow: 0px 0px 7px 0px rgba(0, 0, 0, 0.42);
  box-shadow: 0px 0px 7px 0px rgba(0, 0, 0, 0.42);
}
.day {
  padding-top: 5px;
  display: flex;
  height: 20%;
  margin: 0;
  align-content: flex-start;
  color: rgb(0, 0, 0);
  font-size: 18px;
  font-weight: bold;
}
.icon {
  display: flex;
  margin: 0;
  justify-content: center;
  align-items: center;
  font-size: 70px;
  max-width: 70px;
}
img {
  max-width: 120%;
  max-height: 120%;
  display: block;
  margin: 0 auto;
}
.temperature {
  flex: 1;
  flex-flow: row;
  align-self: flex-end;
  justify-content: center;
  display: flex;
  height: 20%;
  width: 100%;

  color: rgb(128, 128, 128);
}
.temperature .tLow {
  width: 60%;
  justify-content: center;
  align-items: center;
  margin-left: 5px;
  color: rgb(128, 128, 128);
  font-size: 18px;
}
.temperature .tHigh {
  width: 60%;
  margin-right: 5px;
  justify-content: center;
  align-items: center;
  color: rgb(29, 29, 29);
  font-size: 18px;
}
</style>
