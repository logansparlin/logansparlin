<template>
  <div>
    <clone v-if="clone" :data="clone" title="This is the test title"></clone>
    <div class="item-list">
      <div class="item-list-inner">
        <template v-for="(message, index) in messages">
          <item :click="createClone" :title="message"></item>
        </template>
      </div>
    </div>
  </div>
</template>

<script>
  // import axios from 'axios'
  import Clone from './Clone'
  import Item from './Item'

  export default {
    name: 'home',
    data() {
      return {
        intro: 'Supreme',
        messages: null,
        clone: null,
      }
    },
    components: {
      Clone,
      Item,
    },
    created() {
      this.fetchData()
    },
    methods: {
      fetchData() {
        this.messages = ['Title One', 'Title Two', 'Title Three', 'Title Four']
      },
      createClone(event) {
        const position = event.target.getBoundingClientRect()
        const ww = window.innerWidth
        const wh = window.innerHeight
        const scaleX = position.width / ww
        const scaleY = position.height / wh
        this.clone = {
          top: position.top,
          left: position.left,
          width: position.width,
          height: position.height,
          scale: {
            x: scaleX,
            y: scaleY,
          },
        }
      },
    },
  }
</script>

<style lang="scss" scoped>
  .item-list {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    overflow: scroll;
    display: flex;
    justify-content: center;
    align-items: center;
    .item-list-inner {
      white-space: nowrap;
    }
  }
</style>
