<template>
  <div id="app">
    <drawer :show.sync="drawerShow" 
    :pos="pos" 
    :tran="tran"
    @on-hide="onHide"
    @on-show="onShow">
      <div class="layout" slot="drawer" >
        <h2><a href="#">bajian drawer</a></h2>
        <ul>
          <li v-for="item in navItems"><a href="#{{item}}">{{item}}</a></li>
        </ul>
      </div>
      <button v-on:click="directionFlip">directionChange</button><br><br>
      <button v-on:click="tranFlip">tranChange</button><br><br>
      <button v-on:click="drawerToggle">toggle</button>
    </drawer>
  </div>
</template>

<script>
 import Drawer from './components/drawer.vue'
 export default {
   data(){
     return {
       pos: 'left',
       tran: 'overlay',
       drawerShow: false,
       navItems: [
       'decide the width u like',
       'Item2',
       'Item3',
       'Item4',
       'Item5'
       ]
     }
   },
   methods: {
     directionFlip() {
       this.pos=this.pos =='left'?'right':'left'
       setTimeout(()=>{
        this.drawerToggle()
      },500)
     },
     tranFlip() {
       this.tran=this.tran =='overlay'?'push':'overlay'

       setTimeout(()=>{
        this.drawerToggle()
      },0)
     },
     drawerToggle() {
       this.drawerShow=!this.drawerShow
     },
     onHide() {
       console.log('hide');
     },
     onShow() {
       console.log('show');
     }
   },
   components: { Drawer }
 }
</script>

<style>

  *{
    margin: 0px;
    padding: 0px;
  }
  html {
    height: 100%;
  }

  body {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100%;
  }

  #app {
    color: #2c3e50;
    margin-top: -100px;
    max-width: 600px;
    font-family: Source Sans Pro, Helvetica, sans-serif;
    text-align: center;
    background-color: #eee
  }

  #app a {
    color: #42b983;
    text-decoration: none;
  }
  .layout{
    width: 300px;
 }

 button, input[type="button"], a.button {
  color: #fff;
  background-color: #3779d0;
  border: 0;
  font-size: 14px;
  border-radius: 4px;
  padding: 0px 8px;
  height: 40px;
  min-width: 40px;
  line-height: 40px;
  overflow: hidden;
  display: inline-block;
  outline: none;
  -moz-user-select: none;
  -webkit-user-select: none;
  -ms-user-select: none;
  -khtml-user-select: none;
  user-select: none;
  -webkit-transition: all;
  -moz-transition: all;
  transition: all;
  -webkit-transition-timing-function: linear;
  -moz-transition-timing-function: linear;
  transition-timing-function: linear;
  -webkit-transition-duration: .2s;
  -moz-transition-duration: .2s;
  transition-duration: .2s;
}
button:active{
  color: #fff;
  background-color: #377000;
}
</style>
