<template>
  <div>
    <div class="table-layout">
      <div class="table-layout__block">
        <div class="title">
          <div>Stock</div>
          <div>Current</div>
          <div>Change</div>
        </div>
          <Item v-for="item in items"
                :item="item"
                :key="item.stock">
          </Item>
      </div>
    </div>
  </div>
</template>

<script>
import Item from "@/components/Item"

export default {
  name: "InformationBarList",
  components: {
    Item
  },
  props: {
    loading: {
      type: Boolean,
      default: false,
    },
    items: {
      type: Array,
      default: () => [],
    }
  },
}
</script>

<style lang="scss" scoped>
.table-layout {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  &__block {
    width: 300px;
    background-color: #e0e0e0;
    .title {
      display: flex;
      justify-content: space-between;
      font-weight: 600;
      padding: 10px 20px;
      border: 1px solid #c7c7c7;
      line-height: 1;
    }
  }
}
</style>
