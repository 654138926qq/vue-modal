<!--button在组件外-->
<template>
    <div class="modal">
        <transition name="modal">
            <div class="modal-mask" v-show="msg">
                <div class="modal-wrapper">
                    <transition
                            name="modal-container"
                            enter-active-class="animated rubberBand"
                            leave-active-class="animated hinge"
                    >
                        <div class="modal-container" v-show="msg">
                            <div class="modal-header">
                                <slot name="header"></slot>
                            </div>
                            <div class="modal-body">
                                <slot name="body"></slot>
                            </div>
                            <div class="modal-footer">
                                <slot name="footer"></slot>
                                <button class="modal-default-button" @click="closeModal">close</button><!--绑定事件closeModal,且定义$emit触发父组件上的事件-->
                            </div>
                        </div>
                    </transition>
                </div>
            </div>
        </transition>
    </div>
</template>
<style>

    .modal-mask {
            position: fixed;
            z-index: 9998;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, .3);
            display: table;
    }

    .modal-wrapper {
        display: table-cell;
        vertical-align: middle;
    }

    .modal-container {
        width: 300px;
        margin: 0px auto;
        padding: 20px 30px;
        background-color: #fff;
        border-radius: 2px;
        box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
        font-family: Helvetica, Arial, sans-serif;
    }

    .modal-header h3 {
        margin-top: 0;
        color: #42b983;
    }

    .modal-body {
        margin: 20px 0;
    }

    .modal-default-button {
        float: right;
    }

    .modal-enter,.modal-leave-active{
       opacity: 0;
    }
    .modal-enter-active{
        /*opacity: 1;*/
        transition:opacity .5s ease;
    }
    .modal-leave-active{
        opacity: 0;
        transition:opacity 1s ease 2s;
    }
    @import "../assets/css/animate.css";/*引入animate.css库*/
</style>
<script>
    export default{
        name:'modalChild',
        props:['msg'],
        watch:{//观察msg的值变化
           msg:{
              handler(val,oldVal){
                 console.log('modalMsg的值变化为'+val)
              },
           deep:true
           }
        },
        methods:{
           closeModal(){//
              this.$emit('close');//在子组件中触发父组件中的close事件
           }
        }
     }
</script>
