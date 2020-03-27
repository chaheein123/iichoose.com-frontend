<template src="./YelpDialog.html"/>

<script>
import {EventBus} from "../../event-bus.js";
import axios from "axios";

export default {
  name: "YelpDialogue",

  created: function(){
    EventBus.$on("yelpDialogOn", result => {
      let searchKey = Object.keys(result)[0];
      axios
        .get(
          "http://localhost:3000/yelpAPI",
          {
            params: {
              latitude: localStorage.getItem("latitude"),
              longitude: localStorage.getItem("longitude"),
              searchKey
            }
          }
        )
        .then (() => {
          this.dialog = true
        })
    });
  },

  data () {
    return {
      dialog: false,
    }
  },
}
</script>

<style lang="scss" src="./YelpDialog.scss" scoped />