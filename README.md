# wepy-drap
wepy的下拉组件,用的时候自己改改
代码如下:
```js
<!--这是一个下拉框组件-->
<style lang="less">
.drop {
  .inputgroup {
    width: 150rpx;
    height: 50rpx;
    display: flex;
    .input {
      height: 50rpx;
      width: 100rpx;
      font-size: 28rpx;
      text-align: left;
    }
    .iconfont {
      width: 30rpx;
      font-size: 28rpx;
      height: 50rpx;
      line-height: 50rpx;
    }
  }
  .scrol {
    background-color: #ffffff;
    position: absolute;
    width: 150rpx;
    height: 200rpx;
    padding: 10rpx;
    border: #999999;
    .item {
      font-size: 28rpx;
      height: 56rpx;
      line-height: 56rpx;
      text-align: left;
    }
    .active {
      border-bottom: 1px solid #ff8d68;
      color: #ff8d68;
    }
    .inactive {
      border-bottom: 1px solid #999999;
      color: #999999;
    }
  }
}
</style>

<script>
import wepy from 'wepy'
export default class drop extends wepy.component {
  data = {
    active: false,
    activeIndex: 0
  }
  props = {
    list: {},
    width: {}
  }
  methods = {
    select (index) {
      this.activeIndex = index
      this.active = false
      this.$apply()
    },
    open () {
      this.active = !this.active
      this.$apply()
    }
  }
}
</script>
<template>
  <view class="drop">
    <view class="inputgroup"  @tap="open">
      <input class="input"  value={{list[activeIndex]}} disabled=ture />
      <view class="iconfont icon-down"></view>
    </view>
    <scroll-view hidden="{{!active}}" scroll-y class="scrol">
      <block wx:for="{{list}}">
        <view class="item {{index==activeIndex?'active':'inactive'}}" @tap="select({{index}})">{{item}}</view>
      </block>
    </scroll-view>
  </view>
</template>

```
