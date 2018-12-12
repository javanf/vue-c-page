<template>
  <div id="app">
    <page :pageOption="pageOption" :jumpTo="jumpTo"></page>
  </div>
</template>

<script>
import page from './page'
export default {
  name: 'app',
  data () {
    return {
      pageOption: {
        pageNo: 1,
        pageSize: 10,
        total: 152,
        totalPage: 16
      }
    }
  },
  methods: {
    jumpTo(pageNo){
      this.pageOption.pageNo = parseInt(pageNo);
      console.log('当前是第' + pageNo + '页');
      // do something
    }
  },
  components: {
    page
  }
}
</script>

<style lang="scss">
#app{
  padding: 100px;
}
</style>
