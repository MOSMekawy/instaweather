<template>
  <v-app>
    <div id="wrapper">
      <h1>INSTAWEATHER</h1>
      <status-report id="status" />
      <hourly-daily-report id="hdReport" />
    </div>
  </v-app>
</template>

<script>
import status_report from "./components/status_report";
import hourly_daily_report from "./components/houry_daily_report";

export default {
  name: "App",
  components: {
    "status-report": status_report,
    "hourly-daily-report": hourly_daily_report,
  },
};
</script>

    Houry_daily_report
<style>
html,
body {
  width: 100%;
  height: 100%;
  margin: 0px;
  padding: 0px;
  overflow: hidden;
}

@font-face {
  font-family: work-sans-bold;
  src: url("./assets/work-sans-bold.ttf");
}

@font-face {
  font-family: work-sans-medium;
  src: url("./assets/work-sans-medium.ttf");
}

@font-face {
  font-family: work-sans;
  src: url("./assets/work-sans.ttf");
}

.v-application--wrap {
  background: url("./assets/Background.png");
  background-repeat: no-repeat;
  background-size: cover;
}

#wrapper {
  position: absolute;
  top: 38px;
  left: 50%;
  width: calc(100% - 240px);
  height: calc(100% - 147px);
  transform: translateX(-50%);
  font-family: work-sans-bold;
  -webkit-font-smoothing: antialiased !important;
  -moz-osx-font-smoothing: grayscale !important;
  color: white;
}

#wrapper h1 {
  position: absolute;
  top: 0px;
  left: 0px;
  margin: 0px;
  padding: 0px;
}

#status {
  position: absolute;
  top: 212px;
  left: 0px;
  width: 100%;
}

#hdReport {
  position: absolute;
  bottom: 0px;
  left: 0px;
}
</style>
