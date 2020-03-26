<template src="./BottomNav.html"/>

<script>
  import OptionDialog from "../OptionDialog/OptionDialog";
  export default {
    name: "BottomNav",

    components: {
      OptionDialog
    },

    data () {
      return {
        bottomNav: 'recent',
        cuttingMode: false,
        yelpMode: false,
      }
    },

    methods:{
      turnCutterMode: function(){
        this.cuttingMode = !this.cuttingMode
      },
      turnYelpAPI: function(){
        if (this.yelpMode) {
          this.yelpMode = false
        } else {
          navigator.geolocation.getCurrentPosition(pos => {
            localStorage.setItem("latitude", pos.coords.latitude);
            localStorage.setItem("longitude", pos.coords.longitude);
            this.yelpMode = true;
          }, () => {
            alert("Please enable location information for this website in order to use the Yelp recommendation feature")
          }
          )
        }
      }
    }
  }
</script>

<style lang="scss" src="./BottomNav.scss" scoped />