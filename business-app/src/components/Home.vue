<template>
  <div class="weather-card">
    <p>Hello</p>
    <div class="weather-objects">
      <div class="detailed-weather">
        <p class="day">{{ getDaysAhead(1) }}</p>
        <div class="icon">
          <i class="fas fa-sun"></i>
        </div>
        <div class="temperature">
          <div class="tLow">
            <!-- {{ weatherData[0].data.next_6_hours.details.air_temperature_min }} -->
          </div>
          <div class="tHigh">
            {{ getIndecesForAllDays() }}
          </div>
        </div>
      </div>
      <div class="detailed-weather">
        <p class="day">{{ getDaysAhead(2) }}</p>
        <div class="icon">
          <i class="fas fa-cloud-rain"></i>
        </div>
        <div class="temperature">
          <div class="tLow">
            {{
              weatherData[getIndexOfDayOfInterest("2021-09-22T15:00:00Z")].data
                .next_6_hours.details.air_temperature_min
            }}
          </div>
          <div class="tHigh">
            {{
              weatherData[getIndexOfDayOfInterest("2021-09-22T15:00:00Z")].data
                .next_6_hours.details.air_temperature_max
            }}
          </div>
        </div>
      </div>
      <div class="detailed-weather">
        <p class="day">{{ getDaysAhead(3) }}</p>
      </div>
      <div class="detailed-weather">
        <p class="day">{{ getDaysAhead(4) }}</p>
      </div>
      <div class="detailed-weather">
        <p class="day">{{ getDaysAhead(5) }}</p>
      </div>
      <div class="detailed-weather">
        <p class="day">{{ getDaysAhead(6) }}</p>
      </div>
      <div class="detailed-weather">
        <p class="day">{{ getDaysAhead(7) }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import moment from "moment";
export default {
  name: "Home",
  components: {},
  data() {
    return {
      weatherData: [],
      tLowNext1Day: null,
    };
  },

  methods: {
    getIndexOfDayOfInterest(day) {
      const indexForWeatherReport = this.weatherData
        .map(function(e) {
          return e.time;
        })
        .indexOf(day);
      console.log("indexForWeatherReport: " + indexForWeatherReport);
      return indexForWeatherReport;
    },

    getIndecesForAllDays() {
      var indices = [];
      var arr = [
        { time: "2021-09-29" },

        { time: "2021-09-29" },

        { time: "2021-09-30" },
      ];
      // console.log('arr.time '+arr[2]['time'])

      var dateOfInterest = "2021-09-29";
      for(var n=0; n<arr.length; n++){
        if(arr[n]['time'] === dateOfInterest){
          indices.push(n)
        }
      // var idx = arr[n]['time'].indexOf(element);
      // console.log(arr[n]['time'])
      // while (idx != -1) {
      //   indices.push(idx);
      //   idx = arr[n]['time'].indexOf(element, idx + 1);
      // }
    }
    
      console.log('indices '+indices);
    },

    getDaysAhead(daysAhead) {
      return moment()
        .add(daysAhead, "days")
        .format("dddd");
    },
    async fetchWeatherData() {
      const response = await fetch("http://localhost:5002/timeseries");
      const data = await response.json();
      if (response.ok) {
        console.log("Data fetched sucssefully!");
      }
      return data;
    },
  },
  async created() {
    this.weatherData = await this.fetchWeatherData();
    // console.log(this.weatherData[0].data.next_6_hours.details.air_temperature_min)
    moment.locale("nb");
  },
};
</script>

<style scoped>
.weather-card {
  position: absolute;
  margin-left: 25px;
  width: 750px;
  height: 500px;
  border: solid 2px red;
  border-radius: 15px;
  display: flex;
  flex-direction: column;
  flex: 1;
}
.weather-objects {
  margin-top: auto;
  border-radius: 15px;
  border: solid 2px blue;
  height: 30%;
  flex-direction: row;
  display: flex;
  justify-content: stretch;
}
.detailed-weather {
  align-items: center;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-flow: column;
  border: solid 1px green;

  flex: 1;
  border-radius: 15px;
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
  height: 60%;
  width: 100%;
  color: goldenrod;
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
  font-size: 20px;
}
.temperature .tLow {
  width: 50%;
  justify-content: center;
  align-items: center;
  color: rgb(128, 128, 128);
  font-size: 20px;
}
.temperature .tHigh {
  width: 50%;

  justify-content: center;
  align-items: center;
  color: rgb(29, 29, 29);
  font-size: 20px;
}
</style>
