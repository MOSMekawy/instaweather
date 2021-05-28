<template>
  <div class="statusCard">
    <span class="cardTime">Now</span>
    <img src="../assets/cloudy.png" />
    <span class="cardTemp">81</span>
  </div>
</template>

<script>
export default {
  name: "status-card",
};
</script>

<style>
.statusCard {
  display: inline-block;
  position: relative;
  top: 50%;
  width: 68px;
  height: 176px;
  font-family: work-sans;
  text-align: center;
  margin: 0px 40px;
  transform: translateY(-50%);
}

.cardTime {
  font-size: 24px;
}

.statusCard img {
  width: 100%;
  height: auto;
  margin: 5px 0px 10px 0px;
}

.cardTemp {
  position: relative;
  font-size: 36px;
  margin: 0px 0px;
}

.cardTemp::after {
  content: "°";
  position: absolute;
  top: -18px;
  right: -18px;
  font-size: 30px;
}
</style>