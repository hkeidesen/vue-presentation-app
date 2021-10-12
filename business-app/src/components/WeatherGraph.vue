<template>
  <!-- use a function to determine the max and min bound  -->
  <la-cartesian
    :width="750"
    :height="100"
    :bound="[-15, (n) => n + 10]"
    :data="values"
  >
    <la-area
      prop="temperature"
      color="goldenrod"
      animated="truev"
      curve="curveBasis"
      width="2"
    >
      <g slot-scope="props" :fill="props.color">
        <!-- <rect
          :x="props.x - 5"
          :y="props.y - 5"
          width="5"
          height="5"
          >
        </rect> -->
        <text :x="props.x" :y="props.y" text-anchor="middle" dy="-.5em">
          {{ props.value }}
        </text>
      </g>
    </la-area>
    <la-x-axis prop="time" tickSize="5"></la-x-axis>
  </la-cartesian>
</template>

<script>
import { Cartesian, Area, XAxis } from "laue"; //see https://laue.js.org/

export default {
  name: "WeatherGraph",
  props: {
    temperatureDataToPlot: {
      type: Array,
      default: () => [],
    },
  },
  components: {
    LaCartesian: Cartesian,
    // LaLine: Line,
    LaArea: Area,
    LaXAxis: XAxis,
    // LaYAxis: YAxis,
  },
  data () {
    return{
      values: this.temperatureDataToPlot.values
    }
  }
  ,
  mounted() {
    console.log(this.temperatureDataToPlot.values[0]["temperature"]);
  },
};
</script>

<style scoped></style>
