<template>
  <div class="my-counter">
    <button type="button" class="btn btn-light" :disabled="itemGoods.goods_count == 0"
      @click="itemGoods.goods_count > 1 && itemGoods.goods_count--">-</button>
    <input type="number" class="form-control inp" v-model.number="itemGoods.goods_count">
    <button type="button" class="btn btn-light" @click="itemGoods.goods_count++">+</button>
  </div>
</template>

<script>
export default {
  props: {
    itemGoods: {
      type: Object,
      default: () => ({}),
    }
  },
  watch: {
    itemGoods: {
      deep: true,
      handler(val) {
        if (val.goods_count <= 0) {
          val.goods_count = 1
        }
      }
    }
  }
}
</script>

<style lang="less" scoped>
.my-counter {
  display: flex;

  .inp {
    width: 45px;
    text-align: center;
    margin: 0 10px;
  }

  .btn,
  .inp {
    transform: scale(0.9);
  }
}
</style>