<template>

 <transition name="dialog-fade">
    <!-- 对话框的遮罩.self代表只有点击自己才会触发 -->
    <div class="hm-dialog__wrapper" v-show="visible" @click.self="handleClose">
        <!-- 中间显示对话框 -->
        <div class="hm-dialog" :style="{width,marginTop:top}">
            <div class="hm-dialog__header">
                <slot name="title">  <span class="hm-dialog__title">{{title}}</span></slot>

                <!-- 关闭的按钮 -->
                <button class="hm-dialog__headerbtn" @click="handleClose">
                    <i class="hm-icon-close"></i>
                </button>
            </div>
            <!-- 中间的内容 -->
            <div class="hm-dialog__body">
                <!-- 默认插槽 -->
                <slot></slot>
                <!-- <span>这是一段信息</span> -->
            </div>
            <div class="hm-dialog__foter" v-if="$slots.footer">
                <!-- <hm-button>取消</hm-button>
                <hm-button type="primary">确定</hm-button> -->
                <slot name="footer"></slot>
            </div>
        </div>
    </div>
 </transition>
</template>

<script>
export default {
  name: 'HmDialog',
  props: {
    title: {
      type: String,
      default: '提示'
    },
    width: {
      type: String,
      default: '50%'
    },
    top: {
      type: String,
      default: '15vh'
    },
    visible: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    handleClose () {
      console.log('哈哈哈')
      //   this.visible = false
      this.$emit('update:visible', false)
    }
  }
}
</script>

<style lang="scss" scoped>
//scoped会给当前组件的模板中的所有的元素都添加一个随机的属性
//scoped会给当前组件中所有的样式，页添加一个对应的属性选择器
    .hm-dialog__wrapper{
        position:fixed;
        top:0;
        right:0;
        bottom:0;
        left:0;
        overflow: auto;
        margin:0;
        z-index:2001;
        background-color:rgba(0,0,0,.5);
        .hm-dialog{
            position:relative;
            margin:15vh auto 50px;
            background:#fff;
            border-radius:2px;
            box-shadow:0 1px 3px rgba(0,0,0,.3);
            box-sizing:border-box;
            width:30%;
            &__header{
                padding:20px 20px 10px;
                .hm-dialog__title{
                    line-height:24px;
                    font-size:18px;
                    color:#303133;
                }
                .hm-dialog__headerbtn{
                    position: absolute;
                    top:20px;
                    right:20px;
                    padding:0;
                    background:transparent;
                    border:none;
                    outline:none;
                    cursor:pointer;
                    font-size:16px;
                    .el-icon-close{
                        color:#909399;
                    }
                }
            }
            &__body{
                padding:30px 20px;
                color:#606266;
                font-size:14px;
                word-break:break-all;
            }
            &__foter{
                padding:10px 20px 20px;
                text-align:right;
                box-sizing: border-box;
                .hm-button:first-child{
                    margin-right:20px;
                }

            }
        }
    }
    // .dialog-fade-enter-active{
    //     animation:fade .3s;
    // }
    // .dialog-fade-leave-active{
    //     animation:fade .3s reverse;
    // }
    // @keyframes fade{
    //     0%{
    //         opacity:0;
    //         transform:translateY(-20px);
    //     }
    //     100%{
    //         opacity:1;
    //         transform:translateY(0px);
    //     }
    .dialog-fade-enter-active {
  animation: fade .3s;
}

.dialog-fade-leave-active {
  animation: fade .3s reverse;
}

@keyframes fade {
  0% {
    opacity: 0;
    transform: translateY(-20px);
  }
  100% {
    opacity: 1;
    transform: translateY(0px);
  }
    }
</style>
