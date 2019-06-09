<template lang='pug'>
canvas(id="canvas" width="640" height="480")
</template>

<script lang="ts">
let canvas: HTMLCanvasElement;
let context: CanvasRenderingContext2D;

export default {
  mounted() {
    canvas = document.getElementById('canvas') as HTMLCanvasElement!;
    context = canvas.getContext('2d')!;

    canvas.addEventListener('click', this.onClick, false);

    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  },
  methods: {
    onClick(e) {
       var x = e.x;
       var y = e.y;
       // context.fillRect(x, y, 10, 10);
       const r = this.randomInt(0, 255);
       const g = this.randomInt(0, 255);
       const b = this.randomInt(0, 255);


       const ratio =  window.innerWidth / 500;
       const radius = this.randomInt(
         Math.floor(10 * ratio),
         Math.floor(70 * ratio)
       );

       context.beginPath();
       context.fillStyle = `rgb(${r}, ${g}, ${b})`;
       context.arc(x, y, radius, 0, Math.PI*2, false);
       context.fill();
    },
    randomInt(min: number, max: number) {
       return Math.floor(Math.random() * (max - min)) + min;
    }
  }
}
</script>

<style lang="stylus" scoped>
#canvas {
  background: hsl(0, 0%, 90%);
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  width: 100%;
  height: 100%;
}
</style>
