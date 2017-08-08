<template lang="pug">
#AwesomeEmbeddedSlideshow
  .eg-slideshow
    slide(enter='fadeIn' leave='fadeOut').slide-intro
      eg-transition(enter='bounceInRight' leave='bounceOutLeft')
        h3 在遇到直接可视化的问题时，利用聚集可视化解决是个不错的注意

    slide(:steps='2', enter='fadeIn' leave='fadeOut').slide-two
      eg-transition(enter='bounceInLeft' leave='bounceOutRight')
        .div
          h3 聚集可视化不是一种具体的方法
          h4 而是一类将数据预处理的思想
      eg-transition(enter='slideInRight' leave='slideOutRight')
          p.thanks(v-if='step === 2') 首先将收集到的数据分为以下几个维度

    slide(enter='fadeIn' leave='fadeOut').slide-three
      eg-transition(enter='bounceInLeft' leave='bounceOutRight')
        h3 时间(T)、空间(S)、<br />路径(R)、属性值(A)

    slide(enter='fadeIn' leave='fadeOut').slide-four
      eg-transition(enter='bounceInLeft' leave='bounceOutRight')
        h4 所谓聚集可视化就是将这些维度聚集，依据所选维度不同，可以分为 时空和属性聚集(STA)、出发点和目的地聚集(SS)、路径聚集(R)

    slide(:steps='4').slide-five
      eg-transition(leave='fadeOut')
        .subslide(v-if='step === 1')
          h4 最简单的，将这些属性填入到一张表格内让别人看，也勉强算是聚集可视化的一种。
      eg-transition(enter='bounceInDown' leave='bounceOutDown')
        .subslide(v-if='step >= 2')
          h3(v-if='step===2') 而我现在要说的聚集可视化
          h3(v-if='step===3') 就是把这个看上去不专业的表格
          h3(v-if='step===4') 转化成专业的图表
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
        hiThere: 'http://i.imgur.com/ZLT46UN.jpg',
        hopeyoulikeit: 'http://i.imgur.com/N06RFlq.jpg',
        seeAnything: 'http://i.imgur.com/5EuWG4w.jpg',
        OmgEmbedded: 'http://i.imgur.com/wucwFvf.jpg',
        reallyok: 'http://i.imgur.com/qVTNk3Q.jpg',
        thatall: 'http://i.imgur.com/AExXJwF.jpg',
        bunny1: 'http://i.imgur.com/1PL2k1H.jpg',
        bunny2: 'http://i.imgur.com/GfFUcPQ.jpg',
        bunny3: 'http://i.imgur.com/et8w8Rn.gif',
        kitty1: 'https://i.imgur.com/P7iyH.png',
        kitty2: 'http://i.imgur.com/sHOqlJc.jpg',
        kitty3: 'http://i.imgur.com/wiAwNQZ.gif',
        puppy1: 'http://i.imgur.com/Scj7lzM.jpg',
        puppy2: 'http://i.imgur.com/FyFhTEE.jpg',
        puppy3: 'http://i.imgur.com/G62BWuI.gif'
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

#AwesomeEmbeddedSlideshow {
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
      background-image: url('http://i.imgur.com/N06RFlq.jpg');
      background-position: center bottom;
      background-size: 25em;
    }

    .slide-three {
      background-image: url('http://i.imgur.com/5EuWG4w.jpg');
      background-position: center bottom;
      background-size: 30em;
    }

    .slide-four {
      background-image: url('http://i.imgur.com/wucwFvf.jpg');
      background-position: right bottom;
      background-size: 17em;
    }

    .slide-five {
      background-image: url('http://i.imgur.com/qVTNk3Q.jpg');
      background-position: right bottom;
      background-size: 9em;
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
