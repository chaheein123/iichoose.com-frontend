<template src="./OptionDialog.html" />

<script>
import {EventBus} from "../../event-bus";
export default {
  name: "OptionDialog",

  created: function(){
    EventBus.$emit("updatedOptions", this.e7);
  },

  updated: function(){
    if (!this.dialog){
      EventBus.$emit("updatedOptions", this.e7);
    }
  },

  data () {
      return {
        dialog: false,
        e7: ["Bowling",
          "Chinese food",
          "Mcdonalds",
          "Pizza",
          "Tacos"
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
        chip1: true,
      }
  },

  methods: {
    inputEnter(){
      this.e7.push(this.inputValue);
      console.log(this.e7," kekeke");
      this.inputValue = "";

    },
  }

}
</script>
