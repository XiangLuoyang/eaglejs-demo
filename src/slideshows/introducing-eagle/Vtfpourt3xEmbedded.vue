<template lang="pug">
#Vtfpourt3xEmbedded
  .eg-slideshow
    slide(enter='fadeIn' leave='fadeOut').slide-intro
      eg-transition(enter='bounceInRight' leave='bounceOutLeft')
        h3 没关系，<br />我这不是正要帮你推导一下如何得到这九张图吗

    slide(:steps='2', enter='fadeIn' leave='fadeOut').slide-two
      eg-transition(enter='bounceInLeft' leave='bounceOutRight')
        .div
          h3 首先我们约定一下
          h4 圆圈是轨道交通站点，曲线为线路
      eg-transition(enter='slideInRight' leave='slideOutRight')
          p.thanks(v-if='step === 2') 这就是一条轨道的抽象

    slide(:steps='2', enter='fadeIn' leave='fadeOut').slide-three
      eg-transition(enter='bounceInLeft' leave='bounceOutRight')
        h3 对于一条轨道 <br />有以下两个活动
      eg-transition(enter='slideInRight' leave='slideOutRight')
          p.thanks(v-if='step === 2') 别忘了还可以加上时间这个变量

    slide(enter='fadeIn' leave='fadeOut').slide-four
      eg-transition(enter='bounceInLeft' leave='bounceOutRight')
        h4 然后我们在曲线上多加几个圆圈<br />就可以看到。。

    slide(enter='fadeIn' leave='fadeOut').slide-five
      eg-transition(enter='bounceInLeft' leave='bounceOutRight')
      h3 接着 <br /> 要不再加根线?
    slide.slide-six
      h3 要收集的数据类型就这么多了 <br /> 接下来就是选图的问题了
</template>

<script>
import eagle from 'eagle.js'
import ExampleImageSlideshow from './ExampleImageSlideshow'

export default {
  mixins: [eagle.slideshow],
  props: {
    preference: {default: 'baby bunnies'},
    username: {default: 'Tracy'}
  },
  data: function () {
    return {
      preloadedImages: {
        guidaozhandian: '/static/轨道站点.png',
        jinzhanchuzhan: '/static/进站出站.png',
        shangxiazhandian: '/static/上下站点.png',
        duotiaoxianlu: '/static/多条线路.png'
      }
    }
  },
  infos: {
    title: 'Deadpool',
    description: 'Demo embedded slideshow',
    path: 'deadpool'
  },
  components: {
    'example-image-slideshow': ExampleImageSlideshow
  }
}
</script>

<style lang='scss'>
@import url(https://fonts.googleapis.com/css?family=Permanent+Marker);

#Vtfpourt3xEmbedded {
  @import 'node_modules/eagle.js/src/themes/base';
  .eg-slideshow {
    .eg-slide {
      .eg-slide-content, .subslide{
        width: 40em;
        max-width: 80%;
        margin: 0 auto;
        h1, h2, h3, h4, p {
          font-family: 'Permanent Marker', Impact;
          font-weight: normal;
        }
        p.thanks {
          color: gray;
          text-align: right;
          font-size: 1.3em;
        }
        em {
          font-style: normal;
          text-decoration: underline;
        }
      }
      background-repeat: no-repeat;
      background-color: white;
    }

    .slide-intro {
      background-image: url('http://i.imgur.com/ZLT46UN.jpg');
      background-position: center bottom;
      background-size: 28em;
    }
    .slide-two {
      background-image: url('/static/轨道站点.png');
      background-position: center bottom;
      background-size: 25em;
    }

    .slide-three {
      background-image: url('/static/进站出站.png');
      background-position: center bottom;
      background-size: 30em;
    }

    .slide-four {
      background-image: url('/static/上下站点.png');
      background-position: center bottom;
      background-size: 28em;
    }

    .slide-five {
      background-image: url('/static/多条线路.png');
      background-position: center bottom;
      background-size: 25em;
    }

    .slide-six {
      background-image: url('http://i.imgur.com/AExXJwF.jpg');
      background-position: center bottom;
      background-size: 30em;
    }
    #ImageSlideshow {
      position: relative;
      margin: 0 auto;
      width: 16em;
      height: 9em;
      box-shadow: 0 0 0.25em 0.25em #bbb;
    }
  }

}
</style>
