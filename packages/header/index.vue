<template>
  <div :class="{'is-fixed':fixed}" class="i-header">
    <!-- 头部左侧 -->
    <div class="i-header-left">
      <slot name="left">
        <!-- 默认 -->
        <div class="i-header-left-back" @click="historyBack" >
          <span class="ipanelIcon">亃</span>
          <span>返回</span>
        </div>
      </slot>
    </div>

    <!-- 头部title -->
    <span class="i-header-title">
      <slot name="title"></slot>
    </span>

    <!-- 头部右侧 -->
    <div class='i-header-right'>
      <slot name="right"></slot>
    </div>
  </div>
</template>
<script>
  export default {
    name: 'i-header',
    props: {
      fixed: {
        type: Boolean,
        default: true
      }
    },
    methods: {
      historyBack () {
        this.$router.go(-1)
      }
    }
  }
</script>
<style lang="scss" scoped>
  @import '../../src/style/var.scss';

  .i-header{
    position: relative;
    display: flex;
    justify-content: space-around;
    height: 88px;
    width: 100%;
    background: #40caff;
    background: $theme;
    color: #fff;
    border-bottom: 1px solid #f0f0f0;
    overflow: hidden;
    &-left,&-right{
      box-sizing: border-box;
      position: relative;
      width: 20%;
      height: 88px;
      line-height: 90px;
      font-size: 28px;
      text-indent: 20px;
    }
    &-left-back{
      height: 90px;
    }
    &-right{
      text-align: right;
      padding-right: 20px;
    }
    &-title{
      text-align: center;
      width: 50%;
      height: 88px;
      line-height: 88px;
      font-size: 32px;
      @include ellipsis;
    }
  }
</style>