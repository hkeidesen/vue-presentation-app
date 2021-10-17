<template>
  <!-- use a function to determine the max and min bound  -->
  <la-cartesian
    :width="750"
    :height="100"
    :bound="[-15, (n) => n + 10]"
    :data="temperatureDataToPlot"
  >
    <la-area prop="temperature" 
    animated
    curve="curveBumpX">
      <!-- <la-area
      prop="temperature"
      color="goldenrod"
      animated="true"
      curve="curveBumpX"
      :width="2"
    > -->
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
    <la-x-axis prop="time" :tickSize="5"></la-x-axis>
  </la-cartesian>
</template>

<script>
import { Cartesian, Area, XAxis } from "laue"; //see https://laue.js.org

export default {
  name: "WeatherGraph",
  props: {
    temperatureDataToPlot: {
      type: Array,
    },
  },
  components: {
    LaCartesian: Cartesian,
    LaArea: Area,
    LaXAxis: XAxis,
  },
//since the data is being passed from the parent as a prop, there is no need to declare the data is data(){return{data}}!
};
</script>

<style scoped></style>
