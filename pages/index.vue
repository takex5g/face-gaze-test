<template>
  <!-- @mouseup="touchend($event)"
    @mouseleave="touchend($event)" -->
  <div class="bg" @mousemove="touchmove($event)">
    <div class="face-div">
      <img ref="kao" class="face" src="/face.png" width="1292" height="476" />
      <img
        ref="me"
        class="face"
        src="/me.png"
        width="1292"
        height="476"
        :style="{
          transform: `translate(calc(${X}px - 50%), calc(${Y}px - 50%))`,
        }"
      />
    </div>
  </div>
  <!-- 
          transform: `translate(calc(calc(${X}px - 50%) - 50vw), calc(calc(${Y}px - 50%) - 50vh))`, -->
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data() {
    return {
      X: 0,
      Y: 0,
    }
  },
  methods: {
    touchmove(e: MouseEvent) {
      const x = e.x - window.innerWidth / 2
      const y = e.y - window.innerHeight / 2

      // console.log(e.x, e.y, '動かす:', x, y)
      if (x < 25) {
        if (x < -25) this.X = -25
        else this.X = x
      } else this.X = 25

      if (y < 39) {
        if (y < -39) this.Y = -39
        else this.Y = y
      } else this.Y = 39
    },
  },
})
</script>
<style>
#__nuxt,
#__layout {
  width: 100%;
  height: 100%;
}
body {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}
</style>
<style scoped>
.bg {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  overflow: hidden;
}
.face-div {
  margin: auto;
  position: relative;
}
.face {
  transition-duration: 0.5s;
  transform: translate(-50%, -50%);
  transition-timing-function: cubic-bezier(0, 0, 0.06, 0.86);
  display: block;
  position: absolute;
  width: 400px;
  height: auto;
  margin: auto;
}
</style>
