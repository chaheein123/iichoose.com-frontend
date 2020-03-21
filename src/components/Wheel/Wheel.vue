<template src="./Wheel.html" />

<script>
import axios from "axios";

export default {
  name: "Wheel",

  mounted: function(){
    axios
      .get("http://localhost:3000/", {
      params: {
        foods: ["Tacos", "Chinese food", "Mcdonalds", "Pizza", "Bowling"]
      }
      })
      .then(response => {
        this.prizeListOrigin = response.data;
      })
    
  },

  data() {
    return {
      freeze: false,
      rolling: false,
      wheelDeg: 0,
      prizeNumber: 8,
      prizeListOrigin: [],
    };
  },

  computed: {
    prizeList() {
      return this.prizeListOrigin.slice(0, this.prizeNumber);
    },
  },

  methods: {
    onClickRotate() {
      if (this.rolling) {
        return;
      }
      const result = Math.floor(Math.random() * this.prizeList.length);
      this.roll(result);
    },
    roll(result) {
      this.rolling = true;
      const { wheelDeg, prizeList } = this;
      this.wheelDeg =
        wheelDeg -
        wheelDeg % 360 +
        6 * 360 +
        (360 - 360 / prizeList.length * result);
      setTimeout(() => {
        this.rolling = false;
        alert("Result：" + prizeList[result].name);
      }, 4500);
    }
  },

  watch: {
    prizeNumber() {
      this.freeze = true;
      this.wheelDeg = 0;

      setTimeout(() => {
        this.freeze = false;
      }, 0);
    }
  }
}
</script>

<style lang="scss" src="./Wheel.scss" scoped/>