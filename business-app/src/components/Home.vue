<template>
  <div class="weather-card">
    <p>Hello</p>
    <div class="weather-objects">
      <div class="detailed-weather">
        <p class="day">Mon</p>
        <div class="tLow">-2</div>
        <div class="tHigh">5</div>
      </div>
      <div class="detailed-weather">
        <p class="day">Tue</p>
      </div>

      <div class="detailed-weather">
        <p class="day">Wed</p>
      </div>
      <div class="detailed-weather">
        <p class="day">Thur</p>
      </div>
      <div class="detailed-weather">
        <p class="day">Fri</p>
      </div>
      <div class="detailed-weather">
        <p class="day">Sat</p>
      </div>
      <div class="detailed-weather">
        <p class="day">Sun</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.weather-card {
  position: absolute;
  margin-left: 25px;
  width: 45%;
  height: 50%;
  border: solid 2px red;
  border-radius: 15px;
}

.weather-objects {
  position: absolute;
  left: 50%;
  bottom: 2%;
  -webkit-transform: translateX(-50%);
  transform: translateX(-50%);
  border: solid 2px blue;
  width: 98%;
  height: 25%;
  border-radius: 15px;
  display: inline-block;
  justify-content: space-between;
  display: flex;
}
.detailed-weather {
  align-items: center;
  border: solid 1px green;
  width: 13%;
  display: inline-flex;
  flex-direction: row;
  justify-content: space-around;
  border-radius: 15px;
  padding-right: 2%;
}
.detailed-weather .day {
  color: violet;
  position: absolute;
  float: left;
}
</style>
