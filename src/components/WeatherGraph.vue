<template>
  <!-- use a function to determine the max and min bound  -->
  <la-cartesian
    :width="750"
    :height="140"
    :bound="[determineLowestBoundInGraph, (n) => n + 2]"
    :data="temperatureDataToPlot"
  >
    <la-line prop="temperature" 
    animated
    curve="curveBumpX"
    color="#c60000">
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
    </la-line>
    <la-x-axis prop="time" :tickSize="5"></la-x-axis>
  </la-cartesian>
</template>

<script>
import { Cartesian,  XAxis, Line } from "laue"; //see https://laue.js.org

export default {
  name: "WeatherGraph",
  props: {
    temperatureDataToPlot: {
      type: Array,
    },
  },
  methods:{
    determineLowestBoundInGraph(temperatureDataToPlot){
      return Math.min(temperatureDataToPlot)-1
    }
  },
  components: {
    LaCartesian: Cartesian,
    
    LaXAxis: XAxis,
    LaLine: Line
  },
//since the data is being passed from the parent as a prop, there is no need to declare the data is data(){return{data}}!
};
</script>

<style scoped></style>
