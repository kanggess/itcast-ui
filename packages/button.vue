<template>
    <button class="hm-button" :class="[`hm-button--${type}`,{
      'is-plain':plain,
      'is-round':round,
      'is-circle':circle,
      'is-disabled':disabled
    }]"
    :disabled="disabled"
    @click="handleClick">
    <i v-if="icon" :class="icon"></i>
    <!-- 如果没有传入任何的内容，当我们没有传入插槽的时候 -->
      <span v-if="$slots.default"><slot></slot></span>
    </button>
</template>

<script>
export default {
  name: 'HmButton',
  // 封装一个通用的组件，会对props做一个约束，props进行校验
  props: {
    type: {
      // 数据类型：字符串
      type: String
    },
    plain: {
      type: Boolean,
      ddefault: false
    },
    round: {
      type: Boolean,
      default: false
    },
    circle: {
      type: Boolean,
      default: false
    },
    icon: {
      type: String,
      default: ''
    },
    disabled: {
      type: Boolean,
      default: false
    }
  },
  // created () {
  //   console.log(this.type)
  //   console.log(this.$slots)
  // },
  methods: {
    handleClick (e) {
      this.$emit('click', e)
    }
  }
}
</script>

<style lang="scss" >
  .hm-button{
    display:inline-block;
    line-height:1;
    white-space:nowrap;
    cursor:pointer;
    background:#fff;
    border:1px solid #dcdfe6;
    color:#606266;
    -webkit-appearance:none;
    text-align:center;
    box-sizing: border-box;
    outline:none;
    margin:0;
    transition:0.1s;
    font-weight:500;
    //禁止元素的文字被选中
    -moz-user-select:none;
    -webkit-user-select:none;
    -ms-user-select:none;
    padding:12px 20px;
    font-size:14px;
    border-radius:4px;
    &:hover,
    &:focus{
      color:#409eff;
      border-color:#c6e2ff;
      background-color:#ecf5ff;
    }
  }
  .hm-button--primary{
    color:#fff;
    background-color:#409eff;
    border-color:#409eff;
    &:hover,
    &:focus{
      background:#66b1ff;
      border-color:#66b1ff;
      color:#fff;
    }
  }
  .hm-button--success{
    color:#fff;
    background-color:#67c23a;
    border-color:#67c23a;
    &:hover,
    &focus{
      background:#85ce61;
      border-color:#85ce61;
      color:#fff;
    }
  }
  .hm-button--info{
    color:#fff;
    background-color:#909399;
    border-color:#909399;
    &:hover,
    &:focus{
      background:#a6a9ad;
      border-color:#a6a9ad;
      color:#fff;
    }
  }
  .hm-button--warning{
    color:#fff;
    background-color:#e6a23c;
    border-color:#e6a23c;
    &:hover,
    &focus{
      background-color:#ebb563;
      border-color:#ebb563;
      color:#fff;
    }
  }
  .hm-button--danger{
    color:#fff;
    background-color:#f56c6c;
    border-color:#f56c6c;
    &:hover,
    &:focus{
      background:#f78989;
       border-color:#f78989;
      color:#fff;
    }
  }

  .hm-button--primary.is-plain{
    color:#409eff;
    background-color:#d7eafd;
    border-color:#409eff;
    &:hover,
    &:focus{
      background:#66b1ff;
      border-color:#66b1ff;
      color:#fff;
    }
  }
  .hm-button--success.is-plain{
    color:#67c23a;
    background-color:#d8f5c9;
    border-color:#67c23a;
    &:hover,
    &focus{
      background:#85ce61;
      border-color:#85ce61;
      color:#fff;
    }
  }
  .hm-button--info.is-plain{
    color:#909399;
    background-color:#d9e3f8;
    border-color:#909399;
    &:hover,
    &:focus{
      background:#a6a9ad;
      border-color:#a6a9ad;
      color:#fff;
    }
  }
  .hm-button--warning.is-plain{
    color:#e6a23c;
    background-color:#f0e1c8;
    border-color:#e6a23c;
    &:hover,
    &focus{
      background-color:#ebb563;
      border-color:#ebb563;
      color:#fff;
    }
  }
  .hm-button--danger.is-plain{
    color:#f78989;
    background-color:#fff2f0;
    border-color:#f56c6c;
    &:hover,
    &:focus{
      background:#f78989;
       border-color:#f78989;
      color:#fff;
    }
  }
  .hm-button.is-round{
    border-radius:20px;
    padding:12px 23px;
  }
  //原形按钮
  .hm-button.is-circle{
    border-radius:50%;
    padding:12px;

  }
  .hm-button [class*=hm-icon-]+span{
    margin-left:5px;
  }
</style>
