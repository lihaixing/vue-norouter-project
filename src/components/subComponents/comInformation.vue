<template>
  <div>
    {{number}}
    <div>{{activeValue}}</div>
  </div>
</template>

<script>
  export default {
    name: 'com-information',
    // 如果是对象,可以指定传值类型 {number：[number,string,object]}
    props: ['number', 'active-value'],
    data () {
      return {}
    }
  }
</script>

<style scoped>

</style>
