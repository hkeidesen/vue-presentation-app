<template>
  <div class="weather-card">
    <p>Hello</p>
    <div class="weather-objects">
      <div class="detailed-weather">
        <p class="day">Mon</p>
        <div class="icon">
          <i class="fas fa-bolt"></i>
        </div>
        <div class="temperature">
          <class class="tLow">-2</class>
          <class class="tHigh">2</class>
        </div>
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
  /* width: 14%; */
  flex: 1;
  border-radius: 15px;
}
.day {
  padding-top: 5px;
  display: flex;
  height: 20%;
  margin: 0;
  align-content: flex-start;

  /* vertical-align: middle; */
  /* max-width: 50%; */
  /* border: solid 1px black; */

  color: rgb(0, 0, 0);
  font-size: 20px;
  font-weight: bold;
  /* vertical-align: top; */
}
.icon {
  display: flex;
  margin: 0;
  justify-content: center;
  align-items: center;
  font-size: 70px;
  height: 60%;
  width: 100%;
  /* background: coral; */
}
.temperature {
  flex: 1;
  flex-flow: row;
  align-self: flex-end;
  justify-content: center;
  display: flex;
  height: 20%;
  width: 100%;
  /* margin-top: auto; */
  color: rgb(128, 128, 128);
  font-size: 20px;
  
  /* text-align: center; */
}
.temperature .tLow {
  
  width: 50%;
  justify-content: center;
  align-items: center;
  color: rgb(128, 128, 128);
  font-size: 20px;
  /* background: rosybrown; */
}
.temperature .tHigh {
  
  width: 50%;
  /* background: salmon; */
  justify-content: center;
  align-items: center;
  color: rgb(29, 29, 29);
  font-size: 20px;
}
</style>
