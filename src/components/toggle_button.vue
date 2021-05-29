<template>
  <div class="toggle-btn">
    <div class="optionA" v-on:click="clickHandler">
      <span> {{ optionA }}</span>
    </div>
    <div class="optionB" v-on:click="clickHandler">
      <span> {{ optionB }}</span>
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
  cursor: pointer;
}

.optionA,
.optionB {
  position: relative;
  display: inline-block;
  width: 50%;
  height: 100%;
  font-family: work-sans-medium;
  font-size: 24px;
}

.optionA span,
.optionB span {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.selected {
  content: "";
  display: block;
  position: absolute;
  top: 0px;
  left: 2px;
  width: calc(100% / 2);
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