<template>
  <v-app>
    <div id="wrapper">
      <toggle-button id="unitToggle" optionA="C" optionB="F" v-model="unit" />
      <h1 id="appName">INSTAWEATHER</h1>
      <status-report :status="{ ...wData, area }" id="status" />
      <hourly-daily-report
        id="hdReport"
        :hdForcasts="{
          hourly: wData.hourly,
          daily: wData.daily,
        }"
      />
    </div>
  </v-app>
</template>

<script>
import toggle_button from "./components/toggle_button";
import status_report from "./components/status_report";
import hourly_daily_report from "./components/houry_daily_report";
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      unit: true,
      area: "",
      wData: {},
    };
  },
  created: async function () {
    this.fetchWeatherData();
  },
  methods: {
    fetchWeatherData: function () {
      navigator.geolocation.getCurrentPosition(async (location) => {
        let lat = location.coords.latitude;
        let lng = location.coords.longitude;

        let data = await axios.get(
          `http://localhost:3000/weather?lat=${lat}&lng=${lng}&unit=${
            this.$data.unit ? "c" : "f"
          }`
        );

        this.$data.area = data.data.area;
        this.$data.wData = data.data.weather_data;
      });
    },
  },
  watch: {
    unit: function () {
      this.fetchWeatherData();
    },
  },
  components: {
    "status-report": status_report,
    "hourly-daily-report": hourly_daily_report,
    "toggle-button": toggle_button,
  },
};
</script>

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
  top: 150px;
  left: 50%;
  transform: translate(-50%);
}

#hdReport {
  position: absolute;
  bottom: 0px;
  left: 0px;
}

#unitToggle {
  position: absolute;
  top: 0px;
  right: 0px;
}

img {
  -khtml-user-select: none;
  -o-user-select: none;
  -moz-user-select: none;
  -webkit-user-select: none;
  user-select: none;
}

@media only screen and (min-height: 1000px) {
  #status {
    top: 220px;
  }
}

@media (min-width: 721px) and (max-width: 1150px) {
  #wrapper {
    width: calc(100% - 100px);
    height: calc(100% - 76px);
  }
}

@media only screen and (max-width: 720px) {
  #wrapper {
    top: 25px;
    width: calc(100% - 50px);
    height: calc(100% - 50px);
  }

  #unitToggle {
    width: 75px;
    height: 28px;
  } 

  #unitToggle span {
    font-size: 16px;
  }

  #status {
    top: 65px;
  }

  #appName {
    font-size: 18px;
  }
}
</style>
