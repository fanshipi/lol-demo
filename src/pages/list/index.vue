<template>
  <div class="container">
    <ul>
      <li v-for="(item,index) in heroList"
          :key="item.id"
          @click="toDetail(item.id)">
        <img :src="item.iconUrl"
             alt="">
        <span>{{item.name}}</span>
      </li>
    </ul>
  </div>
</template>

<script>
import heroList from '../../data/lol_duowan'
export default {
  data () {
    return {
      heroList
    }
  },
  methods: {
    toDetail (id) {
      wx.navigateTo({ url: `/pages/detail/main?id=${id}` })
    }
  }
}
</script>

<style lang="less" scoped>
.container {
  padding: 0;
}
page {
  background-color: #566a78;
}
ul {
  display: flex;
  flex-wrap: wrap;
}
li {
  width: 33.33%;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 10px;
  img {
    width: 88px;
    height: 88px;
  }
}
</style>