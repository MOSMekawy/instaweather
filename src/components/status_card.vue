<template>
  <div class="statusCard">
    <span class="cardTime">{{ current ? keyword : date }}</span>
    <img :src="require(`../assets/${icon}.png`)" />
    <span class="cardTemp">{{ Math.round(temp) }}</span>
  </div>
</template>

<script>
export default {
  name: "status-card",
  props: {
    time: {
      type: Number,
      required: true,
    },
    temp: {
      type: Number,
      required: true,
    },
    icon: {
      type: String,
      required: true
    },
    hourly: {
      type: Boolean,
      default: true,
    },
    current: {
      type: Boolean,
    },
  },
  computed: {
    date: function () {
      let unix = this.$props.time * 1000;

      let date = new Date(unix);

      if (this.$props.hourly) date = date.getHours() + ":00";
      else date = `${date.getUTCDate()} / ${date.getUTCMonth() + 1}`;

      return date;
    },
    keyword: function () {
      return this.$props.hourly ? "Now" : "Today";
    },
  },
};
</script>

<style>
.statusCard {
  position: relative;
  top: 50%;
  display: inline-block;
  width: 68px;
  height: auto;
  font-family: work-sans;
  margin: auto 40px;
  white-space: normal !important;
  transform: translateY(-50%);
}

.cardTime {
  display: block;
  position: absolute;
  top: -40px;
  left: 50%;
  font-size: 24px;
  white-space: nowrap;
  transform: translateX(-50%);
}

.statusCard img {
  width: 100%;
  height: auto;
}

.cardTemp {
  position: absolute;
  bottom: -50px;
  left: 50%;
  font-size: 36px;
  transform: translateX(-50%);
}

.cardTemp::after {
  content: "°";
  position: absolute;
  top: -6px;
  right: -12px;
  font-size: 30px;
}

@media only screen and (max-width: 720px) {
  .statusCard {
    width: 50px;
  }
  .cardTime {
    top: -30px;
    font-size: 18px;
  }
  .cardTemp {
    bottom: -30px;
    font-size: 18px;
  }
  .cardTemp::after {
    right: -8px;
    font-size: 18px;
  }
}
</style>