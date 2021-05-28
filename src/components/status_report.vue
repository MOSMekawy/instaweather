<template>
  <div class="status">
    <span class="city">New Cairo</span>
    <span class="date">Friday 20th May 2020</span>
    <div class="condition">
      <img class="icon" src="../assets/cloudy.png" />
      <span class="desc">Raining</span>
    </div>
    <div class="temperature">
      <span class="gTemp">702</span>
      <p class="highLow">
        <span class="high">800</span>
        /
        <span class="low">600</span>
      </p>
      <span class="commentary">Clear throughout the day</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "status-report",
  components: {},
};
</script>

<style>
.city {
  margin: 0px 0px 15px 0px;
  font-size: 60px;
  white-space: nowrap;
  letter-spacing: 5px;
}

.date {
  display: block;
  white-space: nowrap;
  font-size: 17px;
  letter-spacing: 2.5px;
  margin: 0px 0px 40px 0px;
}

.condition,
.icon {
  width: 97px;
  height: auto;
}

.desc {
  line-height: 45px;
  font-size: 25px;
  text-align: center;
  white-space: nowrap;
}

.temperature {
  position: absolute;
  top: 20px;
  right: 0px;
  height: 100%;
  font-size: 144px;
}

.gTemp {
  position: relative;
}

.gTemp::after {
  content: "°";
  position: absolute;
  top: -30px;
  right: -45px;
  font-size: 100px;
}

.highLow {
  position: absolute;
  top: 200px;
  right: 0px;
  font-size: 48px;
  font-family: work-sans;
}

.high, .low {
  position: relative;
}

.low {
  opacity: 0.75;
}

.highLow span::after {
  content: "°";
  position: absolute;
  top: -15px;
  right: -20px;
}

.commentary {
  position: absolute;
  top: 280px;
  right: 0px;
  font-size: 24px;
  font-family: work-sans-medium;
  white-space: nowrap;
}
</style>