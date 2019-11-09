<template>
  <div>
    <swiper indicator-dots
            indicator-color="#fff"
            indicator-active-color="#666"
            autoplay
            interval="2000"
            duration="500"
            circular>
      <block v-for=" (item,index) in hero.bgs"
             :key="item">
        <swiper-item>
          <image src="item"></image>
        </swiper-item>
      </block>
    </swiper>
    <view class="main">
      <view class="left">
        <text class="title">{{hero.title}}</text>
        <text class="name">{{hero.name}}</text>
        <view class="tags">
          <text v-for="(item,index) in hero.tags"
                :key="item">{{item}}</text>
        </view>
        <view class="ability">
          <text>生存能力</text>
          <progress percent="hero.Ability.life"
                    stroke-width="12"
                    activeColor="#1ec76b"
                    backgroundColor="#363636"
                    acitve></progress>
          <text>物理攻击</text>
          <progress percent="hero.Ability.physical"
                    stroke-width="12"
                    activeColor="#f2c404"
                    backgroundColor="#363636"
                    active></progress>
          <text>魔法攻击</text>
          <progress percent="hero.Ability.magic"
                    stroke-width="12"
                    activeColor="#f2a709"
                    backgroundColor="#363636"
                    active></progress>
          <text>操作难度</text>
          <progress percent="hero.Ability.difficulty"
                    stroke-width="12"
                    activeColor="#cb8eff"
                    backgroundColor="#363636"
                    active></progress>
        </view>
      </view>

      <view class="right">{{hero.story}}</view>
    </view>
  </div>
</template>

<script>
import heroDetail from '../../data/lol_details_duowan'
export default {
  data () {
    return {
      hero: {}
    }
  },
  onLoad (options) {
    console.log(options)
    let hero = heroDetail.find(v => v.id === options.id)
    this.hero = hero
  }
}
</script>

<style lang="less" scoped>
page {
  background-color: #363636;
}

image {
  width: 100%;
}

.main {
  display: flex;
  color: #fff;
  padding: 12px 10px 0;
}
.left {
  width: 191px;
  display: flex;
  flex-direction: column;
}

.left .title {
  font-size: 14px;
}
.left .name {
  font-size: 18px;
}
.left .tags {
  margin-top: 12px;
}
.left .tags text {
  width: 30px;
  height: 22px;
  background-color: #029b7f;
  display: inline-block;
  font-size: 12px;
  margin-right: 4px;
  border-radius: 4px;
  text-align: center;
  line-height: 22px;
}

.left .ability {
  margin-top: 18px;
}
.left .ability .item {
  display: flex;
}
.left .ability .item text {
  font-size: 14px;
}
.left .ability .item progress {
  width: 100px;
  margin-left: 6px;
}
.right {
  flex: 1;
  font-size: 14px;
}
</style>