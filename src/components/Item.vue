<template>
  <div @click="click" class="item">
    <h4>{{title}}</h4>
  </div>
</template>

<script>
  export default {
    name: 'Item',
    props: {
      title: {
        type: String,
        required: true,
      },
      click: Function,
    },
  }
</script>

<style lang="scss" scoped>
  .item {
    width: 300px;
    height: 300px;
    margin: 0 10%;
    background: white url('../assets/colorado.jpg') no-repeat center center;
    background-size: cover;
    display: inline-block;
    text-align: center;
  }
</style>  