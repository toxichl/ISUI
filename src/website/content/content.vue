<template>
  <div class="content-wrapper">
    <input v-model="ct" type="checkbox" id="ct">
    <div class="sidenav">
      <tree :treeData="nav"></tree>
    </div>
    <section>
      <label for="ct">
        <i class="icon iconfont icon-back"></i>
      </label>
      <div class="iu-router-view">
        <router-view></router-view>
      </div>
    </section>
  </div>
</template>

<script type="text/ecmascript-6">
  import {NAV_METADATA} from '../router/NAV_METADATA'
  import tree from '../tree/tree.vue'
  //    import md from '../markdown/md'
  export default {
    data() {
      return {
        nav: [],
        ct: true
      }
    },
    methods: {
      foldSidebar() {
        this.isSidebarShow = !this.isSidebarShow
      }
    },
    mounted() {
      this.nav = NAV_METADATA
    },
    components: {
      tree
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" scope>
  @import "../../styles/index.styl"
  @import "../pageConfig.styl"

  .content-wrapper
    top $header-height
    position relative
    display flex
    width 100%
    height 100%
    #ct
      width 100%
      display none
      &:checked ~ section
        transition all 0.2s
      &:checked ~ .sidenav
        flex 0 0 0
        width 0
      &:checked ~ section label:before
        content: "展开"
      &:checked ~ section label i
        display inline-block
        transform rotate(180deg)

    .sidenav
      height 100%
      transition all 0.5s
      background $base-sidebar
      width $sidebar-width
      height 100%
      flex 0 0 $sidebar-width
      position relative

    section
      background #fff
      flex 1
      position relative
      transition all 0.3s
      label
        position absolute
        left 10px
        top 10px
        color #777
        font-size 12px
        &:before
          content: '收起'
        i
          font-size 12px
      .iu-router-view
        padding 40px 20px 0 20px

  //    ddd


</style>

