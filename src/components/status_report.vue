<template>
  <div v-if="status.daily" class="status">
    <div class="locale">
      <span class="city">{{ status.area.results[2].address_components[0].short_name }}</span>
      <span class="date">{{ date }} </span>
    </div>
    <div class="condition">
      <img
        class="icon"
        :src="require(`../assets/${status.currently.icon}.png`)"
      />
      <span class="desc">{{ status.currently.summary }}</span>
    </div>
    <div class="temperature">
      <span class="gTemp">{{ Math.round(status.currently.temperature) }}</span>
      <div class="highLow">
        <span class="high">{{
          Math.round(status.daily.data[0].apparentTemperatureHigh)
        }}</span>
        /
        <span class="low">{{
          Math.round(status.daily.data[0].apparentTemperatureLow)
        }}</span>
      </div>
      <div class="commentary">{{ status.daily.data[0].summary }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "status-report",
  props: {
    status: {
      type: Object,
      required: true,
    },
  },
  computed: {
    date: function () {
      let date;

      if (this.$props.status.currently)
        date = new Date(
          this.$props.status.currently.time * 1000
        ).toDateString();

      return date || "";
    },
  },
};
</script>

<style>
.status {
  white-space: nowrap;
  line-height: normal;
  width: 100%;
}

.city {
  margin: 0px 0px 15px 0px;
  font-size: 60px;
  white-space: nowrap;
  letter-spacing: 5px;
}

.locale {
  margin: 0px 0px 35px 0px;
}

.date {
  display: block;
  white-space: nowrap;
  font-size: 17px;
  letter-spacing: 2.5px;
}

.condition,
.icon {
  display: block;
  width: 97px;
  height: auto;
  margin: 0px;
}

.desc {
  display: block;
  line-height: 45px;
  font-size: 25px;
  text-align: center;
  white-space: nowrap;
}

.temperature {
  position: absolute;
  top: 0px;
  right: 0px;
  font-size: 144px;
  white-space: nowrap;
  text-align: right;
}

.gTemp {
  position: relative;
}

.gTemp::after {
  content: "°";
  position: absolute;
  top: -20px;
  right: -45px;
  font-size: 100px;
}

.highLow {
  font-size: 48px;
  font-family: work-sans;
}

.high,
.low {
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
  margin: 15px 0px;
  font-size: 24px;
  font-family: work-sans-medium;
}

@media only screen and (max-width: 1150px) {
  .status {
    display: flex;
    flex-wrap: wrap;
    align-items: flex-start;
    justify-content: space-between;
  }

  .city {
    font-size: 45px;
    white-space: normal;
  }

  .date {
    font-size: 14px;
  }

  .locale {
    order: 1;
    width: 100%;
    margin: 0px;
  }

  .temperature {
    order: 2;
    position: relative;
    text-align: left;
    width: 60%;
  }

  .condition {
    position: relative;
    order: 3;
    width: 39%;
    margin: 10px auto;
    text-align: right;
  }

  .icon {
    width: 100%;
    max-width: 240px;
    display: inline;
  }

  .desc {
    display: none;
  }
}

@media only screen and (max-width: 720px) {
  .city {
    font-size: 25px;
  }
  .date {
    margin: 8px 0px 0px 0px;
    font-size: 13px;
  }

  .gTemp {
    display: block;
    margin: 10px 0px;
    font-size: 80px;
    width: auto;
  }

  .gTemp::after {
    position: relative;
    top: -30px;
    right: 0px;
    font-size: 60px;
  }

  .highLow {
    font-size: 25px;
  }

  .highLow span::after {
    top: -10px;
    right: -10px;
  }

  .condition {
    margin: 0px;
  }

  .icon {
    max-width: 150px;
    margin-top: 0px;
  }

  .commentary {
    font-size: 18px;
  }
}
</style>