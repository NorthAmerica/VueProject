<template>
  <div class="icons">
    <swiper>
      <swiper-slide v-for="(page, index) of pages" :key="index">
        <div class="icon"  v-for="(item) in page" :key="item.id">
          <div class="icon-img">
            <img class="icon-img-content" :src="item.imgUrl"/>
            <p class="icon-desc">{{item.desc}}</p>
          </div>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  props: {
    list: Array
  },
  data () {
    return {
      // iconList: [{
      //   id: '0001',
      //   imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
      //   desc: '景点门票'
      // }, {
      //   id: '0002',
      //   imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/bd/9f7b9b2b60c1502.png',
      //   desc: '踏青赏花'
      // }, {
      //   id: '0003',
      //   imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png',
      //   desc: '必游榜单'
      // }, {
      //   id: '0004',
      //   imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/96/c70f1e85ae4a4f02.png',
      //   desc: '自然风光'
      // }, {
      //   id: '0005',
      //   imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png',
      //   desc: '一日游'
      // }, {
      //   id: '0006',
      //   imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/76/eb88861d78fb9902.png',
      //   desc: '动植物园'
      // }, {
      //   id: '0007',
      //   imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/47/c2b659e048b11602.png',
      //   desc: '主题乐园'
      // }, {
      //   id: '0008',
      //   imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/b8/c5dcdb58deec2402.png',
      //   desc: '湘西凤凰'
      // }, {
      //   id: '0009',
      //   imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/48/cb72b99b71974c02.png',
      //   desc: '生活休闲'
      // }]
    }
  },
  computed: {
    pages () {
      const pages = []
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import "~styles/mixins.styl"
  .icons >>> .swiper-container
    height: 0
    padding-bottom: 50%
  .icon
    position: relative
    overflow: hidden
    float:left
    width:25%
    height: 0
    padding-bottom: 25%
    .icon-img
      position: absolute
      top: 0
      left: 0
      right: 0
      bottom: .44rem
      -webkit-box-sizing: border-box
      -moz-box-sizing: border-box
      box-sizing: border-box
      padding:.1rem
      .icon-img-content
        display: block
        margin: 0 auto
        height: 100%
      .icon-desc
        position: absolute
        top:1.3rem
        left:0
        right:0
        bottom:0
        height:0.4rem
        line-height:0.4rem
        text-align :center
        font-weight: bold
        color: #333
        ellipsis()
</style>
