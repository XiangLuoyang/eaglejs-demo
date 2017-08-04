<template lang='pug'>
.frontpage
  br
  br
  br
  br
  br
  .content
    h1
      span.logo
      span 可视
      span.grey 化
    br
    h2 城市轨道交通客流出行

    p.
      人类从外界获得的信息有80%以上来自于视觉系统。
      人类的创造性不仅取决于逻辑思维，还与形象思维密切相关。
      人类利用形象思维将数据映射为形象视觉符号，从中发现规律，正所谓“一幅图胜过千言万语”。

    p.
      信息时代带给人们前所未有的复杂海量信息，因此，运用直观便捷的数据可视化分析海量数据尤为重要。

    br
    br
    br

    .thumbnails
      .box-card(v-for='slideshow in slideshows')
        router-link(:to='slideshow.infos.path' @click.native="click")
          .embedded-slideshow-container
            component(:is="slideshow", :embedded='true',
                      :keyboardNavigation='false',
                      :mouseNavigation='false')
        .caption
          h3 {{slideshow.infos.title}}
          p.thumbnail-description {{slideshow.infos.description}}
</template>

<script>
import slideshows from 'slideshows/slideshows'

export default {
  data: function () {
    return {
      slideshows: slideshows.list
    }
  },
  mounted: function () {
    console.log(this.slideshows)
    document.currentSlide = {}
  },
  methods: {
    click: function (evt) {
      evt.stopPropagation()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='scss' scoped>
@import "node_modules/eagle.js/src/themes/frontpage/frontpage";
.logo {
  display: inline-block;
  width: 130px;
  height:90px;
  margin-right: 0.1em;
  background-image: url(./logo.svg);
  background-size: contain;
  background-position: center bottom;
  background-repeat: no-repeat;
}

.github-star {
  display: block;
  margin: 0 auto;
  margin-top: -10px;
}
</style>
