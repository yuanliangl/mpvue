<template>
  <div class="my">
    <div class="img">
      <img
        :src="userimg"
        alt
      />
      <span v-text='username'></span>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      userimg: '',
      username: '',
      list: []
    }
  },
  mounted () {
    this.getuser()
  },
  methods: {
    getuser () {
      let that = this
      wx.getUserInfo({
        success: function (res) {
          console.log(res)
          that.userimg = res.userInfo.avatarUrl
          that.username = res.userInfo.nickName
          console.log(that.userimg)
        }
      })
    }
  },
  onLoad (options) {
    console.log('动态参数', options)
    wx.login({
      success (res) {
        if (res.code) {
          wx.request({
            // url: 'https://tcb-api.tencentcloudapi.com',
            data: {
              code: res.code
            }
          })
        } else {
          console.log('登录失败！' + res.errMsg)
        }
      }
    })
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
.my {
  width: 100%;
  height: 100%;
}
.img {
  background: red;
}
.img > img {
  margin: 0 auto;
  display: block;
  width: 80px;
  height: 80px;
  border-radius: 50%;
}
</style>