<template>
  <body>
    <div>
      {{
        getAllTemperaturesForTheDay(getDaysAhead(1)["dateAhead"].slice(0, 10))
      }}
    </div>
  </body>
</template>

<script>
// import * as d3 from 'd3';
import moment from "moment";

export default {
  name: "WeatherGraph",
  props: {
    temperatureDataToPlot: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      weatherData: [],
    };
  },
  methods: {
    getAllTemperaturesForTheDay(dateOfInterest) {
      //this function is used to get the max and min temperature for a certain day
      // create an empty array, which is is used to store the indexes of the array for a certain day,
      // i.e.: if the day 2021-09-22 has index 1,2,...,n, the index will be stored here.

      var temp_array = [];
      // uses the weatherData array that is obtained from the met.no-api call
      var arr = this.temperatureDataToPlot;

      // console.log('arr.time '+arr[2]['time'])
      for (var n = 0; n < arr.length; n++) {
        if (arr[n]["time"].slice(0, 10) === dateOfInterest) {
          temp_array.push(
            this.temperatureDataToPlot[n].data.instant.details.air_temperature
          );
        }
      }

      // console.log('max_temp', Math.max(...temp_array))
      // console.log('temp', temp_array)
      console.log("temp_array", temp_array);
      return temp_array;
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
      return { dateNameAhead, dateAhead };
    },
  },
};
</script>
