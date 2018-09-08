<template>
  <div>{{welcome}}{{x}}</div>
</template>

<script>
  export default {
    name: 'A',
    props: ['x'],
    data () {
      return {
        welcome: 'hello,I am component A!'
      }
    }
  }
</script>

<style scoped>

</style>
