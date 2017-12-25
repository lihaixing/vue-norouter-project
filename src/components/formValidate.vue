<template>
  <div>
    <!--
    修改器
    lazy会延时,number,trim
    -->
    <input type="text" v-model="single_value">{{single_value}}
    <div>
      <input type="checkbox" name="" v-model="checkbox_value" value="apple">
      <input type="checkbox" name="" v-model="checkbox_value" value="banana">
      <input type="checkbox" name="" v-model="checkbox_value" value="pean">
      {{checkbox_value}}
    </div>
    <div>
      <input type="radio" name="" v-model="radio_value" value="男">
      <input type="radio" name="" v-model="radio_value" value="女">
      {{radio_value}}
    </div>
    <div>
      <select name="" v-model="selection">
        <option v-for="(v,k) in selectOptions" :value="v.value">{{v.text+'-'+k}}</option>
      </select>{{selection}}
    </div>
    日期：{{dateNow}}
  </div>
</template>

<script>
  export default {
    name: 'form-validate',
    data: function () {
      return {
        single_value: '',
        checkbox_value: [],
        radio_value: '',
        selection: null,
        selectOptions: [
          {
            text: '苹果',
            value: 'apple'
          },
          {
            text: '香蕉',
            value: 'banana'
          },
          {
            text: '梨',
            value: 'pean'
          }
        ]
      }
    },
    computed: {
      // 日期不能实时更新
      dateNow () {
        return new Date()
      }
    }
  }
</script>

<style scoped>

</style>
