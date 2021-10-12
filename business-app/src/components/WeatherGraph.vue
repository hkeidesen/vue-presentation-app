<template>
  <la-cartesian :width="750" :height="100" narrow :bound="[0, n => n + 5]" :data="values">
    <la-area prop="temperature">
      <g
        slot-scope="props"
        :fill="props.color">
        <rect
          :x="props.x - 5"
          :y="props.y - 5"
          width="5"
          height="5">
        </rect>
        <text
          :x="props.x"
          :y="props.y"
          text-anchor='middle'
          dy="-.5em">
          {{ props.value }}
        </text>
      </g>
    </la-area>
    <la-x-axis prop="time"></la-x-axis>
    <la-y-axis></la-y-axis>
  </la-cartesian>
</template>

<script>
import { Cartesian, Area } from "laue";

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
  },
  data: () => ({
    values: [
      { time: '00:01', temperature: 3.8 },
      { time: '00:02', temperature: 4.1 },
      { time: '00:03', temperature: 3.8 },
      { time: '00:04', temperature: 3.5 },
      { time: '00:05', temperature: 4.2 },
      { time: '00:06', temperature: 4.4 },
      { time: '00:07', temperature: 3.9 },
      { time: '00:08', temperature: 4.2 },
      { time: '00:09', temperature: 5.4 },
      { time: '00:10', temperature: 5.9 },
    //   { time: '00:11', temperature: 8.0 },
    //   { time: '00:12', temperature: 8.1 },
    //   { time: '00:13', temperature: 8.1 },
    //   { time: '00:14', temperature: 8.1 },
    //   { time: '00:15', temperature: 6.9 },
    //   { time: '00:16', temperature: 7.2 },
    //   { time: '00:17', temperature: 7.0 },
    //   { time: '00:18', temperature: 6.1 },
    //   { time: '00:19', temperature: 6.0 },
    //   { time: '00:20', temperature: 5.7 },
    ],
  }),
};
</script>

<style scoped></style>
