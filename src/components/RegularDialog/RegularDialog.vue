<template src="./RegularDialog.html"/>

<script>
import {EventBus} from "../../event-bus.js";
// import axios from "axios";

export default {
  name: "RegularDialog",

  created: function(){
    EventBus.$on("regularDialogOn", (value) => {
      this.resultName = Object.keys(value.resultKey)[0];
      this.resultImg = value.resultImg;
      this.resultIndex = value.resultIndex;
      this.dialog = true;
    });
  },

  data () {
    return {
      dialog: false,
      resultName: null,
      resultImg: null,
      resultIndex: null,
    }
  },

  methods: {
    eliminateClick: function(){
      EventBus.$emit("eliminateOption", this.resultIndex);
      this.dialog = false;
    }
  }
}
</script>

<style lang="scss" src="./RegularDialog.scss" scoped />