<!--button在组件内-->
<template>
    <div class="modal">
        <button @click="showModal">模态框</button>
        <transition name="modal">
            <div class="modal-mask" v-show="showContainer">
                <div class="modal-wrapper">
                    <transition
                            name="modal-container"
                            enter-active-class="animated rubberBand"
                            leave-active-class="animated hinge"
                    >
                        <div class="modal-container" v-show="showContainer">
                            <div class="modal-header">
                                <h3 name="header">header</h3>
                            </div>
                            <div class="modal-body">
                                <h3 name="body">body</h3>
                            </div>
                            <div class="modal-footer">
                                <h3 name="footer">footer</h3>
                                <button class="modal-default-button" @click.stop="showModal">close</button>
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
        transition:opacity 1s linear 2s;
    }
    @import "../assets/css/animate.css";/*引入animate.css库*/
</style>
<script>
    export default{
        name:'modal',
        data () {
            return{
                showContainer:false
            }
        },
        methods:{
            showModal:function(){
                this.myModal=!this.myModal;
            },
            showModal1:function(){
                if(this.showContainer){
                    this.showContainer=false;
                }else{
                    this.showContainer=true;
                }
            }
        }
    }
</script>
