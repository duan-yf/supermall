<template>
  <div class="goods">
    <goods-list-item v-for="item in goods" :key="item.good" :goods-item="item"></goods-list-item>
    
  </div> 
</template>
  
<script>
  import GoodsListItem from './GoodsListItem'
  
  export default {
    name: 'GoodsList',
    props: {
      goods: {
        type: Array,
        default() {
          return []
        }
      }
    },
    components: {
      GoodsListItem
    },
    data () {
      return {
        
    }
    }
 }
</script>
 
<style scoped>
  .goods {
    display: flex;
    flex-wrap: wrap;
    /* 默认nowrap */
    justify-content: space-around;
    background-color: var(--color-background);

    padding: 2px;
  }
</style>