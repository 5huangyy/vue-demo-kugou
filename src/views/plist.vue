<template>
  <div class="container plist">
    <mt-cell v-for="(item,index) in plist" :title="item.title" is-link :label="item.countPlay" :to="item.location">
      <img slot="icon" :src="item.imgUrl" width="60" height="60">
    </mt-cell>
  </div>
</template>

<script type="es6">
  import { Cell,Indicator } from 'mint-ui'
  import list_plist from '../jsons/list_plist'
  export default {
    data(){
      return {
        plist: []
      }
    },
    created(){
      this.getList()
    },
    methods: {
      getList(){
        Indicator.open({
          text: '加载中...',
          spinnerType: 'snake'
        });
        this.parseList(list_plist)
      },
      parseList(data){
        setTimeout(()=> {
          Indicator.close()
          this.plist = data;
        }, 1000)
      }
    }
  }
</script>

<style scoped>
  .mint-cell {
    padding: 10px 0 !important;
  }

  .mint-cell-title img {
    margin-right: 5px !important;
  }
</style>
