<template lang="pug">
.eg-slideshow
  image-slide(v-for='imageUrl, i in images[preference]',
              :enter="(i === 0) ? null : 'slideInRight'", leave='slideOutLeft', :url='imageUrl')
</template>

<script>
import eagle from 'eagle.js'

export default {
  mixins: [eagle.slideshow],
  props: {
    preference: {default: 'funny kitties'}
  },
  data: function () {
    var images = {
      'baby bunnies': [
        '/static/聚集可视化.png',
        '/static/特征化1.png',
        '/static/特征化2.png'
      ],
      'funny kitties': [
        'https://i.imgur.com/P7iyH.png',
        'http://i.imgur.com/sHOqlJc.jpg',
        'http://i.imgur.com/wiAwNQZ.gif'
      ],
      'fluffy puppies': [
        'http://i.imgur.com/Scj7lzM.jpg',
        'http://i.imgur.com/FyFhTEE.jpg',
        'http://i.imgur.com/G62BWuI.gif'
      ]
    }
    return {
      images: images,
      preloadedImages: images[this.preference]
    }
  }
}
</script>
