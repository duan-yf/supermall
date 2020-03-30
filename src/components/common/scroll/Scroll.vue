<template>
  <div class="wrapper" ref="wrapper">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>
  
<script>
  import Bscroll from 'better-scroll'
  
  export default {
    name: 'Scroll',
    props: {
      probeType: {
        type: Number,
        default: 0
      },
      pullUpLoad: {
        type: Boolean,
        default: false
      }
    },
    components: {
      
    },
    data () {
      return {
        scroll: null
    }
    },
    methods: {
      //返回顶部
        scrollTop(x, y, time = 300) {
            //给它在外面做一层封装, 给它设置一个默认的滚动时间，300毫秒;
            this.scroll.scrollTo(x, y, time)
        },
    },
    mounted() {
      //1.创建Bscroll对象
      this.scroll = new Bscroll(this.$refs.wrapper, {
        click: true, //默认是false
        probeType: this.probeType,
        pullUpLoad: this.pullUpLoad
      })
      //2.监听滚动的位置
      if(this.probeType === 2 || this.probeType === 3 ) {
        this.scroll.on('scroll', (position) => {
        // console.log(position);
        this.$emit('scroll', position)
      })
      }
      //3.监听scroll滚动到底部
      if(this.pullUpLoad) {
        this.scroll.on('pullingUp', () => {
          this.$emit('pullingUp')
          
        })
      }
    },
    methods: {
      //返回顶部
      scrollTo(x, y, time = 300) {
          //给它在外面做一层封装, 给它设置一个默认的滚动时间，300毫秒;
          this.scroll && this.scroll.scrollTo(x, y, time);
      },
      finishPullUp() {
        this.scroll.finishPullUp()
      },
      refresh() {
        this.scroll && this.scroll.refresh()
      },
      finishPullUp() {
        this.scroll && this.scroll.finishPullUp()
      },
      getScrollY() {
        return this.scroll ? this.scroll.y : 0
      }
    }
 }
</script>
 
<style scoped>
  
</style>