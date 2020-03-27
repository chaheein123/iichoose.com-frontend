<template src="./LandingPage.html"/>

<script>
import Wheel from "../../components/Wheel/Wheel";
import BottomNav from "../../components/BottomNav/BottomNav";
import YelpDialogue from "../../components/YelpDialog/YelpDialog.vue";
import RegularDialog from "../../components/RegularDialog/RegularDialog.vue"
// import {EventBus} from "../../event-bus.js";

export default {
  name: "LandingPage",

  components: {
    Wheel,
    BottomNav,
    YelpDialogue,
    RegularDialog,
  },
}
</script>

<style lang="scss" src= "./LandingPage.scss" scoped />
