<template>
  <view class="index">
    <Counter />
    <!-- 使用组件库这里做一下区分
    react需要引入，并且是大写使用
    vue不需要引入，并且是小写使用 -->
    <button style="margin-top: 10px;" @tap="requestData" type='primary'>按钮</button> 
    
  </view>
</template>

<script>
import './index.scss'
import Counter from '../../components/Counter.vue'
import Taro from '@tarojs/taro'
// import { Button } from '@tarojs/components' //react这样使用


export default {
  name: 'Index',
  components: {
    Counter
  },
  methods:{
    requestData(){
      console.log("我点击了请求数据");
      //进行数据请求
      Taro.request({
          url:'https://api2.jirengu.com/city.php'
      }).then(res=>{
          console.log(res.data)
      })
    }
  }
}
</script>
