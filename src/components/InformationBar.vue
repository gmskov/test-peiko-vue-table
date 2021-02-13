<template>
  <div>
    <button @click="getData" :disabled='isDisabled'>Get data</button>
    <InformationBarList v-if="!loading && items.length" :items="items"/>
    <div v-if="loading">Loading...</div>
    <div v-if="error"> no data </div>
  </div>
</template>

<script>
import simulateAsyncReq from "@/plugins/getDataFunc";
import { payload } from "@/mocData";
import InformationBarList from "./InformationBarList";

export default {
  name: "InformationBar",
  components: {
    InformationBarList
  },
  data: () => ({
    loading: false,
    items: [],
    error: ''
  }),
  computed: {
    isDisabled: function(){
      return this.loading;
    }
  },
  methods: {
    async getData() {
      this.loading = true;
      this.error = null;
      this.items = [];

      simulateAsyncReq(payload).then( data => {
        let items = []
        data.stocks.forEach(( item, index ) => {
          let element = {};
          element.stock = item;
          element.start = payload.start[index]
          element.current = payload.current[index].toFixed(2)
          items.push(element)
        })
        this.items = items.sort(( a, b ) => ( a.stock > b.stock ) ? 1 : (( b.stock > a.stock ) ? -1 : 0 ));
        this.loading = false;
      })
      .catch(() => {
        this.error = "Some error happened"
      })
      .finally(() => {
        this.loading = false;
      })
    }
  },
}
</script>

<style scoped>
button {
  margin-bottom: 20px;
  padding: 5px 20px;
  border: 1px solid #efefef;
  border-radius: 5px;
}
</style>