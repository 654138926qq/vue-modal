<template>
  <div id="app">
      <h1>.vue组件方式的模态框</h1>
      <button @click="showModal">模态框</button>
      <modal-child :msg="myModal" @close="closeModal"><!--将myModal的值传给绑定的属性msg--><!--close监听子组件触发的事件-->
          <h2 slot="header">header</h2>
          <h3 slot="body">body</h3>
          <h3 slot="footer">footer</h3>
      </modal-child>
  </div>
</template>

<script>
import ModalChild from 'components/ModalChild'

export default {
  name: 'app',
  components: {
     ModalChild
  },
  data () {
     return {
         myModal:false
     }
  },
  watch:{
     myModal:{
        handler:function(val,oldVal){
           console.log('myModal的值变化为'+val)
        },
        deep:true
     }
  },
  methods:{
     showModal:function(){
         if(this.myModal){
             this.myModal=false;
             console.log('关闭模态框');
         }else{
             this.myModal=true;
             console.log('打开模态框');
         }
     },
     closeModal:function(){//定义close的事件函数
         this.myModal=false;
     }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
