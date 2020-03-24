<template src="./OptionDialog.html" />

<script>
import {EventBus} from "../../event-bus";
import Vue from "vue";

export default {
  name: "OptionDialog",

  props: ["cuttingMode", "yelpMode"],

  created: function(){
    let optionList = this.e7.map(option => Object.keys(option)[0]);
    EventBus.$emit("updatedOptions", {optionList});
    EventBus.$on("wheelDone", result => {
      if (this.cuttingMode){
        this.e7.splice(result,1)
      }
    })
  },

  updated: function(){
    if (!this.dialog){
      let optionList = this.e7.map(option => Object.keys(option)[0]);
      EventBus.$emit("updatedOptions", {optionList, cuttingMode:this.cuttingMode});
    }
  },

  data: function () {
    return {
      dialog: false,
      e7: [
        {"Bowling":true},
        {"Chinese food":true},
        {"Mcdonalds":true},
        {"Pizza":true},
        {"Tacos":true}
      ],
      options: [
        "Angus Steakhouse",
        "Ann",
        "Apple Bees",
        "Asian",
        "Blonde",
        "Bowling",
        "Brunette",
        "Chick-fil-a",
        "Chinese food",
        "Chipotle",
        "Donuts",
        "El Taco Tote",
        "Five Guys",
        "Fried chicken",
        "Jamba juice",
        "Japan",
        "Korea",
        "Mcdonalds",
        "Milk tea",
        "Pizza",
        "Pho",
        "Popeyes",
        "Redheads",
        "Tacos",
      ],
      inputValue: "",
    }
  },

  methods: {
    inputEnter(){
      let obj = {};
      obj[this.inputValue] = true;
      this.e7.push(obj);
      this.inputValue = "";
    },
    chipsChange(index,item){
      let obj = {};
      obj[Object.keys(item)[0]] = false;
      Vue.set(this.e7, index, obj);
      this.e7.splice(index,1);
    }
  }
}
</script>