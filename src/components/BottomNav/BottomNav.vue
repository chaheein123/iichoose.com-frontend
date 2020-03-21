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
      }
    },
  }
</script>