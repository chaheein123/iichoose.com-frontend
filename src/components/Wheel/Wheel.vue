<template src="./Wheel.html" />

<script>
import axios from "axios";
import {EventBus} from "../../event-bus";

export default {
  name: "Wheel",

  data() {
    return {
      freeze: false,
      rolling: false,
      wheelDeg: 0,
      prizeNumber: 8,
      prizeListOrigin: [],
      afterDone: false,
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
        // alert("Result：" + prizeList[result].name);
        EventBus.$emit("wheelDone", result);
        
      }, 4500);
    }
  },

  created: function(){
    EventBus.$on("updatedOptions", updatedOptions => {
      let modifiedPrizeList = this.prizeListOrigin.map(option => option.name);
      if (JSON.stringify(updatedOptions.optionList) != JSON.stringify(modifiedPrizeList)){
        if (updatedOptions.cuttingIndex == undefined || updatedOptions.cuttingIndex == null){
          axios
            .get("http://localhost:3000/", {
            params: {
              foods: updatedOptions.optionList
            }
            })
            .then(response => {
              this.prizeListOrigin = response.data;
            })
        } else {
          this.prizeListOrigin.splice(updatedOptions.cuttingIndex,1);
        }
      }
    });
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
