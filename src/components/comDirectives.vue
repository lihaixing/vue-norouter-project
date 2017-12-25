<template>
  <div>
    <p v-color="'red'">我是自定义指令color</p>
    <p v-color="fontColor">我是自定义指令color</p>
    <input type="text" v-focus>
  </div>
</template>

<script>
  export default {
    name: 'com-directives',
    data () {
      return {
        'fontColor': 'blue'
      }
    },
    directives: {
      // binding 是一个对象,name(color),value,
      // oldValue(指令绑定的前一个值，近在update和componentUpdated钩子中使用)
      // expression(绑定值的字符串形式)
      // arg(传给指令的参数) 例如 v-color:foo foo就是参数
      color (el, binding) {
        el.style.color = binding.value
      },
      focus: {
        inserted (el, binding) {
          el.focus()
        }
      },
      // 更具体，带钩子函数
      background: {
        bind (el, binding) {

        },
        inserted (el) {

        }

      }
    }
  }
</script>

<style scoped>

</style>
