<template>
  <div class="item-layout">
      <div> {{ item.stock }} </div>
      <div> {{ item.current }} </div>
      <div :class="[isNegative ? 'negative' : 'positive']">
        {{ countChanges(item) | sign }}
      </div>
  </div>
</template>

<script>
export default {
  name: "Item",
  props: {
    item: {
      type: Object,
      default: () => {},
    }
  },
  data: () => ({
    isNegative: false
  }),
  methods: {
    countChanges(item) {
      let value = (item.current - item.start).toFixed(2);
      this.isNegative = value < 0;
      return value;
    }
  },
  filters: {
    sign(value) {
      return value >= 0 ? `+${value}` : value
    },
  },
}
</script>

<style lang="scss" scoped>
.item-layout {
  display: flex;
  justify-content: space-between;
  padding: 10px 20px;
  border: 1px solid #c7c7c7;
  line-height: 1;
  background-color: #fff;
  border-top: none;
  .positive {
    color: #3cab29;
  }
  .negative {
    color: #e72d2d;
  }
}
</style>
