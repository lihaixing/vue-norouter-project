<template>
  <div>
    好好学习天天向上
    <!--插槽一旦被设置了name,就不是默认插槽了-->
    <slot>父组件无内容时显示</slot>
    <slot name="header">父组件无header内容时显示</slot>
  </div>
</template>

<script>
export default {
  name: 'slot-component'
}
</script>

<style scoped>

</style>
