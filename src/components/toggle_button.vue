<template>
  <div class="toggle-btn">
    <div class="optionA" v-on:click="clickHandler">
      {{ optionA }}
    </div>
    <div class="optionB" v-on:click="clickHandler">
      {{ optionB }}
    </div>
    <div class="selected" :class="{ toggle: !value }"></div>
  </div>
</template>

<script>
export default {
  name: "toggle-button",
  props: {
    optionA: {
      type: String,
      required: true,
    },
    optionB: {
      type: String,
      required: true,
    },
    value: {
      type: Boolean,
      default: true,
      required: true,
    },
  },
  methods: {
    clickHandler: function () {
      this.$emit("input", !this.$props.value);
    },
  },
};
</script>

<style>
.toggle-btn {
  position: relative;
  width: 152px;
  height: 48px;
}

.optionA,
.optionB {
  position: relative;
  display: inline-block;
  width: 76px;
  height: 100%;
  font-family: work-sans-medium;
  text-align: center;
  line-height: 2;
  font-size: 24px;
}

.selected {
  content: "";
  display: block;
  position: absolute;
  top: 0px;
  left: 2px;
  width: 74px;
  height: 100%;
  background-color: rgba(255, 255, 255, 0.25);
  transform: translate3d(0%, 0, 0);
  transition: transform 200ms ease-in-out;
  border-left: 2px solid white;
}

.toggle {
  transform: translate3d(100%, 0, 0);
  transition: transform 200ms ease-in-out;
}
</style>