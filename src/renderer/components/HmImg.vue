<template>
  <img :src="base" alt="">
</template>

<script>
import { getImg } from '@/jbot/img.js'

const baseImg = 'data:image/jpeg;base64,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'

export default {
  name: 'hm-img',

  props: ['url'],

  data () {
    return {
      base: baseImg
    }
  },

  watch: {
    url (val) {
      if (val) {
        getImg(val).then(res => {
          if (res) {
            // console.log('watch 成功')
            this.base = res
          } else {
            // console.log('watch 失败')
            this.base = baseImg
          }
        }).catch(() => {
          this.base = baseImg
        })
      }
    }
  },

  mounted () {
    if (this.url) {
      getImg(this.url).then(res => {
        if (res) {
          // console.log('mounted 成功')
          this.base = res
        } else {
          // console.log('mounted 失败')
          this.base = baseImg
        }
      }).catch(() => {
        this.base = baseImg
      })
    }
  }
}
</script>

<style scoped>
img {
  width: 40px;
  height: 40px;
  border-radius: 20px;
  overflow-y: hidden;
}
</style>

