<template>
  <div id="clone" class="fadeIn" :style="{ transform: 'translate3d(' + data.left + 'px, ' + data.top + 'px, 0) scaleX(' + data.scale.x + ') scaleY(' + data.scale.y + ')' }">
    <div class="inner">
    </div>
  </div>
</template>

<script>
  import dynamics from 'dynamics.js'

  export default {
    name: 'clone',
    props: {
      data: {
        type: Object,
        default() {
          return {
            left: 0,
            top: 0,
            width: 0,
            height: 0,
            scale: {
              x: 0,
              y: 0,
            },
          }
        },
      },
    },
    mounted() {
      dynamics.animate(this.$el, {
        scaleX: 1,
        scaleY: 1,
      }, {
        type: dynamics.easeOut,
        duration: 400,
        friction: 94,
      })
    },
  }
</script>

<style lang="scss" scoped>
  #clone {
    background: white url('../assets/colorado.jpg') no-repeat center center;
    background-size: cover;
    width: 100%;
    height: 100%;
    position: absolute;
    z-index: 10;
    transform-origin: 0 0;
  }
</style>