<template>
  <div>
    <h2>组件传递信息</h2>
    <input type="text" v-model="myValue">
    <com-information number="5" :active-value="myValue"></com-information>

    <h2>组件插槽</h2>
    <slot-component>
      <p>我是插槽内容1</p>
      <p slot="header">我是header插槽内容</p>
      <p>我是插槽内容2</p>
    </slot-component>

    <h2>动态组件</h2>
    <!--动态组件和路由很像，如router-view-->
    <!--keep-alive可以使动态组件缓存起来-->
    <!--<keep-alive>-->
      <p :is="currentView"></p>
    <!--</keep-alive>-->
    <button @click="switchComponent">切换组件</button>

  </div>
</template>

<script>
  import comInformation from './subComponents/comInformation'
  import slotComponent from './subComponents/slotComponent'

  var comIs1 = {
    template: '<div>{{message}}</div>',
    data: function () {
      return {
        message: 'hello, i am com-is1'
      }
    }
  }
  var comIs2 = {
    template: '<div>{{message}}</div>',
    data: function () {
      return {
        message: 'hello, i am com-is2'
      }
    }
  }
  export default {
    name: 'component-all',
    data () {
      return {
        myValue: '李海兴',
        currentView: 'comIs1'
      }
    },
    components: {
      comIs2,
      comIs1,
      comInformation,
      slotComponent
    },
    methods: {
      switchComponent () {
        this.currentView === 'comIs1' ? this.currentView = 'comIs2' : this.currentView = 'comIs1'
      }
    }
  }
</script>

<style scoped>

</style>
