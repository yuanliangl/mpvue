<template>
  <div class="shop">
    <img :src="shopBg"/>
    <h2>店铺</h2>
    <button @tap="call">打电话</button>
  </div>
</template>

<script>
import shopBg from '@/utils/img'
export default {
  data () {
    return {
      shopBg
    }
  },
  methods: {
    call () {
      wx.makePhoneCall({
        phoneNumber: '15770593425'
      })
    }
  }
}
</script>

<style>

</style>