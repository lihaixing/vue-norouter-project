<template>
  <div>
    <div>我是自定义事件组件</div>
    <button @click="emitMyEvent">触发自定义事件</button>
  </div>
</template>

<script>
  export default {
    name: 'my-event',
    data: function () {
      return {
        message: '自定义事件的参数'
      }
    },
    methods: {
      emitMyEvent () {
        this.$emit('my-define-event', this.message)
      }
    }
  }
</script>

<style scoped>

</style>
