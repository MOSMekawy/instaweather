<template>
  <div v-if="hdForcasts.hourly" class="hdWrap">
    <v-tabs
      class="hdTabs"
      background-color="transparent"
      color="white"
      dark
      v-model="tab"
    >
      <v-tab>Hourly</v-tab>
      <v-tab>Daily</v-tab>
    </v-tabs>

    <div class="anotherWrap">
      <transition name="slide-x-transition">
        <div v-if="tab === 0" class="anotherCardContainer" key="hourly">
          <div class="cardContainer">
            <status-card
              v-for="(elm, i) in hourlyReport"
              :key="elm.time"
              :time="elm.time"
              :temp="elm.temperature"
              :icon="elm.icon"
              :current="i == 0"
              :hourly="true"
            />
          </div>
        </div>

        <div v-else class="anotherCardContainer" key="daily">
          <div class="cardContainer">
            <status-card
              v-for="(elm, i) in hdForcasts.daily.data"
              :key="elm.time"
              :time="elm.time"
              :temp="elm.temperatureHigh"
              :icon="elm.icon"
              :current="i == 0"
              :hourly="false"
            />
          </div>
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
import status_card from "./status_card";

export default {
  name: "hourly-daily-report",
  data() {
    return {
      tab: 0,
    };
  },
  props: {
    hdForcasts: {
      type: Object,
      required: true,
    },
  },
  computed: {
    hourlyReport: function () {
      return this.$props.hdForcasts.hourly.data.slice(0, 23) || [];
    },
  },
  components: {
    "status-card": status_card,
  },
};
</script>

<style>
.anotherWrap {
  height: calc(100% + 5px);
  overflow: hidden;
}

.hdWrap {
  width: 100%;
  height: 249px;
  border-top: 1px solid white;
  border-bottom: 1px solid white;
}

.hdWrap > .statusCard:first {
  margin: 0px 14px 0px 40px;
}

.hdTabs {
  position: absolute;
  top: 0px;
  left: 0px;
  transform: translateY(-100%);
}

.v-tab {
  text-transform: none !important;
  padding: 0px !important;
  font-size: 18px !important;
}

.anotherCardContainer {
  width: 100%;
  height: calc(100% + 25px);
  overflow: hidden;
}

.cardContainer {
  width: calc(100% + 17px);
  height: calc(100% - 27px);
  overflow: scroll;
  white-space: nowrap;
}

.cardContainer::-webkit-scrollbar {
  transform: translateY(-50%);
  height: 6px;
}

.cardContainer::-webkit-scrollbar-track {
  border-radius: 10px;
}

.cardContainer::-webkit-scrollbar-thumb {
  height: 6px;
  border-radius: 4px;
  background-color: white;
}

.cardContainer::-webkit-scrollbar-button {
  display: none;
}

@media only screen and (max-width: 720px) {
  .hdWrap {
    height: 150px;
  }

  .v-tab {
    font-size: 15px !important;
  }
}
</style>