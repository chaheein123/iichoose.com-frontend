<template src="./YelpDialog.html"/>

<script>
import {EventBus} from "../../event-bus.js";
import axios from "axios";

export default {
  name: "YelpDialogue",

  created: function(){
    EventBus.$on("yelpDialogOn", result => {
      let searchKey = Object.keys(result)[0];
      this.searchKey = searchKey;
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
        .then ((response) => {
        
          this.results = response.data.result;
          this.dialog = true;
        })
        .catch(() => {
          return;
        })
    });
  },

  data () {
    return {
      searchKey: "",
      dialog: false,
      results: null,
      error: false,
    }
  },
}
</script>

<style lang="scss" src="./YelpDialog.scss" scoped />