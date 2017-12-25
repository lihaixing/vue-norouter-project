<template>
  <div>
    <!--过渡动画包括css过渡和js过渡-->
    <transition name="fade">
      <div v-show="isShow">我是show-fade</div>
    </transition>

    <!--多元素过渡，如果标签相同，需要key值区分-->
    <transition name="fade">
      <div v-if="isShow" key="1">我是if-fade</div>
      <div v-else key="2">我是else-fade</div>
    </transition>

    <transition name="myTran">
      <div v-show="isShow">我是show-myTran</div>
    </transition>
    <button @click="isShow=!isShow">toggleShow</button>

    <!--注意mode模式可以让组件先进后出、先出后进，默认进出是同时进行的-->
    <!--组件切换是多元素过渡, v-if和v-else也可实现多元素过渡-->
    <transition name="myTranCom" mode="out-in">
      <p :is="currentView"></p>
    </transition>
    <button @click="switchCom">toggleCom</button>

  </div>
</template>

<script>
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
    name: 'com-transition',
    data () {
      return {
        isShow: true,
        currentView: 'comIs1'
      }
    },
    methods: {
      switchCom () {
        this.currentView === 'comIs1' ? this.currentView = 'comIs2' : this.currentView = 'comIs1'
      }
    },
    components: {
      comIs1,
      comIs2
    }
  }
</script>

<style scoped>
  /*css过渡效果就是这四个类名实现的*/
  .fade-enter {
    opacity: 0
  }

  .fade-leave {
    opacity: 1
  }

  .fade-enter-active {
    transition: all 0.5s ease-in-out;
  }

  .fade-leave-active {
    opacity: 0;
    transition: all 0.5s ease-in-out;
  }

  /*myTran*/
  .myTran-enter {
    opacity: 0;
    transform: translateY(-500px);
  }

  .myTran-leave {
    opacity: 1
  }

  .myTran-enter-active {
    transition: all 0.5s ease-in-out;
  }

  .myTran-leave-active {
    opacity: 0;
    transform: translateY(500px);
    transition: all 0.5s ease-in-out;
  }

  /*myTranCom*/
  .myTranCom-enter {
    opacity: 0;
    transform: translateY(-500px);
  }

  .myTranCom-leave {
    opacity: 1
  }

  .myTranCom-enter-active {
    transition: all 0.5s ease-in-out;
  }

  .myTranCom-leave-active {
    opacity: 0;
    transform: translateY(500px);
    transition: all 0.5s ease-in-out;
  }
</style>
