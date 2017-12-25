<template>
  <div>
    <transition
      v-on:before-enter="beforeEnter"
      v-on:enter="enter"
      v-on:after-enter="afterEnter"
      v-on:enter-cancelled="enterCancelled"

      v-on:before-leave="beforeLeave"
      v-on:leave="leave"
      v-on:after-leave="afterLeave"
      v-on:leave-cancelled="leaveCancelled"
    >
      <div class="ifDev" v-if="isShow">我是if</div>
    </transition>
    <button @click="isShow=!isShow">toggleShow</button>
  </div>
</template>

<script>
  export default {
    name: 'transition-js',
    data () {
      return {
        isShow: true
      }
    },
    methods: {
      // 进入中 el表示里面的元素div
      beforeEnter: function (el) {
        $(el).css(
          {
            transform: 'translateX(-500px)',
            opacity: 0
          }
        )
      },
      // 此回调函数是可选项的设置
      // 与 CSS 结合时使用
      enter: function (el, done) {
        $(el).animate({
          left: 0,
          opacity: 1
        }, {
          duration: 500,
          complete: done
        })
      },
      afterEnter: function (el) {
        // ...
      },
      enterCancelled: function (el) {
        // ...
      },

      // --------
      // 离开时
      // --------

      beforeLeave: function (el) {
        // ...
      },
      // 此回调函数是可选项的设置
      // 与 CSS 结合时使用
      leave: function (el, done) {
        $(el).animate({
          left: '500px',
          opacity: 0
        }, {
          duration: 500,
          complete: done
        })
        done()
      },
      afterLeave: function (el) {
        // ...
      },
      // leaveCancelled 只用于 v-show 中
      leaveCancelled: function (el) {
        // ...
      }
    }
  }
</script>

<style scoped>
  .ifDev{
    width:100%;
    position:absolute;
  }
  button{
    margin-top:50px;
  }
</style>
