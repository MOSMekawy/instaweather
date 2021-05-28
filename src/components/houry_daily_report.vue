<template>
  <div class="hdWrap">
    <v-tabs class="hdTabs" background-color="transparent" color="white" dark>
      <v-tab>Hourly</v-tab>
      <v-tab>Daily</v-tab>
    </v-tabs>
    <status-card />
    <status-card />
  </div>
</template>

<script>
import status_card from "./status_card";

export default {
  name: "hourly-daily-report",
  components: {
    "status-card": status_card
  },
};
</script>

<style>
.hdWrap {
  width: 100%;
  height: 250px;
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
</style>