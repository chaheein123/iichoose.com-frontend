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
        yelpMode: true,
      }
    },

    methods:{
      turnCutterMode: function(){
        this.cuttingMode = !this.cuttingMode
      },
      turnYelpAPI: function(){
        this.yelpMode = !this.yelpMode
      }
    }
  }
</script>