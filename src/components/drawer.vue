<template>
  <!-- container -->
  <div class="vue-drawer">
    <div :style="{'transform': 'translate3d('+translateX+'px,0,0)'}"
    class="main">
    <!-- main body -->
    <slot></slot>
    <!-- mask -->
    <div class="mask" :class="show ? 'active' : ''" @click="hideMask"></div>
  </div>
  <div v-el:drawer class="drawer" 
  :class="[pos!='left' ? 'drawer-right' : 'drawer-left', show ? 'active' : '']" >
    <!-- drawer -->
    <slot name="drawer"></slot>
  </div>
</div> 
</template>

<script >

 export default {
   props: {
     show: {
       type: Boolean,
       default: false
     },
     pos: {
       type: String,
       default: 'left'
     },
     tran: {
       type: String,
       default: 'overlay'
     }
   },
   data() {
     return {
      drawerWidth:0,
      translateX:0
    }
  },
  watch:{
    show:function(){
      //listener
      if (!this.show)
        this.$emit('on-hide');
      else
        this.$emit('on-show');

      //transition
      if (this.tran=='overlay') return;
      if (!this.show)
        this.translateX=0
      else
        this.translateX=this.pos=='left'?this.drawerWidth:-this.drawerWidth
    }
  },
  ready(){
    this.drawerWidth=this.$els.drawer.clientWidth
  },
  methods: {
   hideMask() {
     this.show = false;
   }
 }
}
</script>

<style scoped>
 .vue-drawer {
   display: block;
   position: absolute;
   top: 0;
   left: 0;
   width: 100%;
   height: 100%;
   overflow: hidden;
 }

 .vue-drawer > .main {
   position: absolute;
   top: 0;
   left: 0;
   right: 0;
   bottom: 0;
   transition: transform ease-in-out 0.38s, visibility 0.38s;
 }

 .vue-drawer > .main > .mask {
   position: absolute;
   top: 0;
   left: 0;
   right: 0;
   bottom: 0;
   visibility: hidden;
   opacity: 0;
   transition: opacity ease-in-out 0.38s, visibility ease-in-out 0.38s;
   background-color: rgba(0, 0, 0, 0.3);
 }

 .vue-drawer > .main > .active {
   visibility: visible;
   opacity: 1;
 }

 .vue-drawer > .drawer {
   background-color: #fff;
   position: fixed;
   top: 0;
   height:100%;
   overflow: hidden;
   pointer-events: none;
   visibility: hidden;
   transition: transform ease-in-out 0.38s, visibility 0.38s;
   will-change: none;
 }

 .vue-drawer > .drawer-left {
   left: 0;
   transform: translateX(-102%);
 }

 .vue-drawer > .drawer-right {
   right: 0;
   transform: translateX(102%);
 }


 .vue-drawer > .active {
   pointer-events: inherit;
   visibility: visible;
   transform: translateX(0%);
 }
</style>
