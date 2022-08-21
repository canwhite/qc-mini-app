<template>
  <view class="content">
    <image class="logo" src="/static/logo.png" />
    <view class="text-area">
      <text class="title">{{ title }}</text>
      <view class="btn" @click="requestData" style="margin-top:10px"> 
        request
      </view>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref } from 'vue'
const title = ref('Hello')

/** 
 * 这里稍微补充一下热更新
 * taro的时候取dist文件就可以，然后就是在config/dev
 * mini: {
 *    hot:true  ,//编译配置，配置热更新
 * },
 * uni的使用需要取build的dev里取最终的打包项目
 * 
 */
function requestData(){
    uni.request({
      url: 'https://api2.jirengu.com/city.php', 
        success: (res) => {
          console.log("--res--",res);
        }
    });
}
</script>

<style>
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.btn{
  display: flex;
  justify-content: center;
  align-items: center;
}

.logo {
  height: 200rpx;
  width: 200rpx;
  margin-top: 200rpx;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 50rpx;
}

.text-area {
  display: flex;
  justify-content: center;
}

.title {
  font-size: 36rpx;
  color: #8f8f94;
}
</style>
