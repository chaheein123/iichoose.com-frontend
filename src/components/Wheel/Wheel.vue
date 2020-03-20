<template src="./Wheel.html" />

<script>
export default {
  name: "Wheel",

  data() {
    return {
      freeze: false,
      rolling: false,
      wheelDeg: 0,
      prizeNumber: 8,
      prizeListOrigin: [
        {
          icon: "https://picsum.photos/40?random=1",
          name: "$10000"
        },
        {
          icon: "https://picsum.photos/40?random=6",
          name: "Thank you!"
        },
        {
          icon: "https://picsum.photos/40?random=2",
          name: "$500"
        },
      ],
      // options: {
      //   options: [
      //     "Korean",
      //     "Fastfood",
      //     "Mexican",
      //     "Japanese",
      //     "Thai",
      //     "Chinese",
      //     "Fried Chicken",
      //     "Italian",
      //     "Bowling",
      //     "Hiking",
      //     "Ethiopian",
      //     "Taiwanese"
      //   ],
      // }
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
      console.log(this.prizeList[result]["name"])
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
        alert("Result：" + prizeList[result].name);
      }, 4500);
    }
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