<template>
  <div
    class="bg"
    @mousemove="touchmove($event)"
    @mouseup="touchend($event)"
    @mouseleave="touchend($event)"
  >
    <div class="bgimg"></div>

    <!-- <div class="mediv"> -->
    <div
      class="me"
      :style="{
        left: X - 350 + 'px',
        top: Y - 130 + 'px',
      }"
    ></div>
    <!-- </div> -->
  </div>
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
    touchmove(e) {
      this.X = e.x
      this.Y = e.y
      // return
      if (e.x < 486) {
        if (e.x < 410) this.X = 410
        else this.X = e.x
      } else this.X = 486

      if (e.y < 273) {
        if (e.y < 136) this.Y = 136
        else this.Y = e.y
      } else this.Y = 273
      console.log('pageX:', e.x, e.y)
      console.log('touchmove:', e)
    },

    touchend(e) {
      // this.Y = e.clientY
      // this.X = e.screenX
      // this.Y = e.screenY
      // console.log('offsetX:', e.offsetX)
      // console.log('touchend:', e)
    },
    touchend(e) {
      // this.X = e.offsetX
      // this.Y = e.offsetX
      // this.X = e.screenX
      // this.Y = e.screenY
      // console.log('offsetX:', e.offsetX)
      // console.log('touchend:', e)
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
  position: relative;
  overflow: hidden;
}
.bgimg {
  background-image: url('/face.png');
  top: calc(50% - 130px);
  left: calc(50% - 350px);
  background-size: contain;
  background-repeat: no-repeat;
  width: 100%;
  max-width: 700px;
  height: 260px;
  position: absolute;
}
.me {
  background-image: url('/me.png');
  top: calc(50% - 130px);
  left: calc(50% - 350px);
  background-size: contain;
  background-repeat: no-repeat;
  width: 100%;
  max-width: 700px;
  height: 260px;
  position: absolute;
  transition-duration: 0.5s;
}
.mediv {
  overflow: hidden;
}
</style>
