<template>
   <div class="backScroll">
      <!--<i class="iconfont icon-moreunfold"></i>-->
      <img src="../../assets/top.png" />
   </div>
</template>
<script>
    import Scroll from './backScroll'
    export default {
        mixins:[Scroll],
        props:{
           flag:{
              type:Boolean,
              default:false
           }
        },
        methods:{
          onScroll(){
              const  scroller=this.scroller;
              const  isWindow= (scroller===window);
              const height= Math.ceil(window.screen.height/2);
              const scrollTop=isWindow? scroller.scrollY:scroller.scrollTop;
              //监听页面滑动位置，如果页面滑动过半就显示按钮
              if(scrollTop>height){
                 this.$store.commit('CHANGE_CIRCLE_FLAG',true);
              }else {
                 this.$store.commit('CHANGE_CIRCLE_FLAG',false);
              }
          }
        }
    }
</script>

<style lang="less" scoped>
@import "../../assets/fz";
@import "../../assets/icons/iconfont";
  div{
      z-index: 99999;
      position: fixed;
     .fz(right,60);
     .fz(bottom,120);
     border-radius: 75%;
     background-color: whitesmoke;
     opacity: 1;
    //翻转180
    /*transform: rotate(180deg);*/
    /*-webkit-transform: rotate(180deg);*/
    //box-shadow: 0px 0px #888888;
    -webkit-filter: drop-shadow(1px,1px,1px,#888888);
    filter:drop-shadow(1px,1px,1px,#888888);
    /*i{*/
       /*color: #a7a7a7;*/
    /*}*/
  }
  .iconfont::before{
     .fz(font-size,80);
  }

</style>
