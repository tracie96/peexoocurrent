<template>
    <div>
     <transition name="modal">
        <div class="modal-mask" v-show="show">
            <div class="modal-container">
                <div class="modal-dialog" role="document">
                    <div class="modal-content">
                        <div class="text-center mt-3">
                            <span><i :icon="icon" class='peexo-highlight-text fa-3x' :class="[{'fa': true}, icon ? 'fa-' + icon : '']"></i></span>
                        </div>
                        <div class="alert-contain">
                            <p class="text-inside text-center" :caption="caption">
                              {{caption}}
                            </p>
                            <p class="text-center peexo-body-text" :nextlineCaption="nextlineCaption">
                                {{nextlineCaption}}
                            </p>
                            
                         <div class="text-center mb-5 mt-4">
                                <button @click="close" style="border-radius: 5px !important;padding: 0 40px !important;"
                                    class="mr-3 btn btn-rounded btn-peexoo text-white" :cancelbtnText="cancelbtnText">{{cancelbtnText}}
                                </button>
                                <button @click="handleSubmit" style="border-radius: 5px !important"
                                    class="btn btn-rounded btn-peexoo text-white" :submitbuttonText="submitbuttonText" >{{submitbuttonText}}
                                </button>
                            </div>

                        </div>
                    </div>
                </div>
            </div>
        </div>
    </transition>
</div>
</template>

<script>
    
    export default {
        name: "makepayment",
        props: ['show','caption', 'nextlineCaption','cancelbtnText', 'submitbuttonText','icon' ],
        components: {   },

        data: function () {
            return {
                 
                
            }
        },
        mounted: function () {
            document.addEventListener("keydown", (e) => {
                if (this.show && e.keyCode == 27) {
                    this.close();
                }
            });
        },
        methods: {
            close: function () {
                this.$emit('close');
            },
            handleSubmit: function(){
                this.$emit('submit-modal');
                 
            }
            
        }
    }
</script>
<style scoped>
    .modal-mask {
        position: fixed;
        z-index: 9998;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, .5);
        transition: opacity .3s ease;
    }

    .modal-content {
        padding-left: 30px !important;
        padding-right: 30px !important;
        background: #FFFDF7 !important
    }

    .log {
        color: #b58000 !important;
    }

    .modal-enter {
        opacity: 0;
    }

    .modal-leave-active {
        opacity: 0;
    }

    .modal-enter .modal-container,
    .modal-leave-active .modal-container {
        -webkit-transform: scale(1.1);
        transform: scale(1.1);
    }

    .close-btn {
        position: absolute;
        right: -1rem;
        top: -1rem;
        z-index: 1000;
        background: #d8d8d8;
        border-radius: 50%;
        height: 40px;
        width: 40px;
        color: #4f4f4f;
        font-weight: normal;
        padding: 10px 12px;
    }

    .fa-times {
        font-size: 20px;
    }
    .width-15 {
        width: 15% !important;
    }

    .width-85 {
        width: 85% !important;
    }
    .modal-container {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background: rgba(0, 0, 0, 0.3) !important;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    #confirm-modal {
        background: #fefbf3;
    }

    .alert-contain p.text-inside {
        font-family: 'Montserrat';
        font-size: 16px;
        font-weight: normal;
        color: #4d4d4d !important;
        padding: 10px 0 10px;
    }
    .btn.btn-peexoo{
        padding: 0 20px !important;
        text-transform: none !important
    }
    p{
        margin-bottom: 0 !important;
    }
</style>