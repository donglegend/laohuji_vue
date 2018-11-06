<template>
  <div class="stage">
    <meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no">
    <div class="list game1111">
      <div class="colitem"></div>
      <div class="colitem"></div>
      <div class="colitem"></div>
    </div>
  </div>
</template>

<script>
import animate from './animateplus';

export default {
  data() {
    return {
      elColItemHeight: 0,
      ANGLE: [
        [3, 6, 0], // 0
        [2, 2, 2], // 1
        [0, 0, 0], // 2
        [7, 7, 7], // 3
        [9, 9, 9], // 4
        [8, 8, 8], // 5
        [5, 5, 5], // 6
        [6, 6, 6], // 7
        [1, 1, 1], // 8
        [3, 3, 3], // 9
        [4, 4, 4], // 10
      ],
    };
  },
  methods: {
    getRandom(n, m) {
      return Math.floor(Math.random() * (m - n + 1) + n);
    },
    getDomRect(dom) {
      return document.querySelector(dom).getBoundingClientRect();
    },
    run(arr) {
      const u = 136;
      animate({
        elements: '.colitem',
        duration: index => 5000 + index * 1000,
        easing: 'in-out-cubic',
        'background-position-y': index => ['0px', u * 60 - u * arr[index]],
      }).then(() => {});
    },
    initGameScale() {
      this.gameScale = window.innerWidth / 750;
      document.querySelector('.game1111').style.transform = `scale(${
        this.gameScale
      })`;
    },
  },
  mounted() {
    this.initGameScale();
    setTimeout(() => {
      this.run(this.ANGLE[this.getRandom(1, 10)]);
    }, 300);
  },
};
</script>

<style>
.list {
  transform-origin: 0% 0%;
  transform: scale(0.5);
  width: 396px;
  height: 136px;
  background: rgba(0, 255, 0, 0.4);
}
.colitem {
  float: left;
  width: 126px;
  height: 136px;
  margin-right: 3px;
  background: url(./luck_types.png) repeat-y 0px 0px;
  background-size: 100%;
}
</style>

