<template>
  <div id="app">
    <MyHeader :title="'我的购物车'" backgroundColor="red" color="green"></MyHeader>
    <div style="margin-top: 45px">
      <MyGoods v-for="item in list" :key="item.id" :item="item"></MyGoods>
    </div>
    <MyFooter :arr="list"></MyFooter>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader'
import MyGoods from './components/MyGoods'
import MyFooter from './components/MyFooter'

export default {
  components: {
    MyHeader,
    MyGoods,
    MyFooter
  },
  data() {
    return {
      list: []
    }
  },
  created() {
    this.$axios({
      url: "/api/cart"
    }).then((res) => {
      console.log(res);
      this.list = res.data.list
    })
  }
}
</script>