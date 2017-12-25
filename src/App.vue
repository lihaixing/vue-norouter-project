<template>
  <div id="app">
    <!--<img src="./assets/logo.png">-->
    <!--<HelloWorld/>-->
    <h2>过渡动画css</h2>
    <transition-css></transition-css>

    <h2>过渡动画js</h2>
    <transition-js></transition-js>

    <h2>自定义指令</h2>
    <com-directives></com-directives>

    <h2>组件循环</h2>
    <component-a v-for="(v,k) in list" :key="k"></component-a>
    <button @click="addItem">addItem</button>

    <h1>对象、数组循环</h1>
    <ul>
      <li v-for="(v,k) in list">{{v.name+'-'+k}}</li>
      <li v-for="(v,k) in obj">{{v+'-'+k}}</li>
    </ul>

    <h2>样式 :class/:style</h2>
    <div :class="className">我是验证样式className的div</div>
    <div :class="className2" :style="myStyle">我是验证样式className2的div</div>

    <h2>v-if、v-show、v-else</h2>
    <ul>
      <!--v-if隐藏，元素会不存在，v-show隐藏元素仍然存在-->
      <li v-if="is_if">我是if</li>
      <li v-else>我是else</li>
      <li v-show="!is_if">我是show</li>
    </ul>

    <h2>事件修改器</h2>
    <!--stop,13,-->
    <input type="text" @keydown.enter="onKeyDown">

    <h2>自定义事件</h2>
    <my-event @my-define-event="onMyEvent"></my-event>

    <h2>表单</h2>
    <form-validate></form-validate>

    <h2>组件</h2>
    <component-all></component-all>
  </div>
</template>

<script>
  // import HelloWorld from './components/HelloWorld'
  import A from './components/A'
  import myEvent from './components/myEvent'
  import formValidate from './components/formValidate'
  import componentAll from './components/componentAll'
  import transitionCss from './components/comTransition'
  import transitionJs from './components/transitionJs'
  import comDirectives from './components/comDirectives'

  export default {
    name: 'app',
    data: function () {
      return {
        list: [
          {name: '李海兴'},
          {name: '李海丽'}
        ],
        obj: {
          name: 'lihaixing',
          age: 29
        },
        className: {
          red_font: true,
          blue_font: false
        },
        className2: [
          'class1',
          'class2',
          {
            'class3': true,
            'class4': false
          }
        ],
        myStyle: {
          'color': 'red',
          'font-size': '18px'
        },
        is_if: false
      }
    },
    methods: {
      addItem () {
        // push会触发更新，但直接为某个key赋值或改变数组长度是不会触发更新的，
        // 可以用vue.set(this.list,key,value)
        this.list.push({
          name: 'father'
        })
      },
      onKeyDown () {
        console.log('你按下了enter键')
      },
      onMyEvent (message) {
        console.log('触发了自定义事件')
        console.log(message)
      }
    },
    components: {
      // HelloWorld,
      componentA: A,
      myEvent,
      formValidate,
      componentAll,
      transitionCss,
      transitionJs,
      comDirectives
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
