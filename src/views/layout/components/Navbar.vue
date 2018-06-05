<template>
  <el-menu class="navbar" mode="horizontal">
    <div class="nav-left">
      <logo></logo>
    </div>
    <div class="nav-right">
       <div class="avatar-wrap">
          <img class="user-avatar" :src="avatar+'?imageView2/1/w/80/h/80'">
          <el-tag>{{name}}</el-tag>
        </div>
        <span @click="logout()"><svg-icon icon-class="logout" class-name="logOut" /></span>
    </div>
    </el-menu>
</template>

<script>
import { mapGetters } from 'vuex'
import Logo from '@/components/Logo'

export default {
  components: {
    Logo
  },
  computed: {
    ...mapGetters([
      'sidebar',
      'avatar',
      'name'
    ])
  },
  methods: {
    logout() {
      this.$store.dispatch('LogOut').then(() => {
        location.reload() // 为了重新实例化vue-router对象 避免bug
      })
    }
  }
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
@import "../../../styles/variables.scss";
.navbar {
  line-height: 100px;
  border-radius: 0px !important;
  background-color: $menuBg;
  padding: 0 30px;
  .nav-left {
    height: 100%;
    float: left
  }
  .hamburger-container {
    line-height: 58px;
    height: 50px;
    float: left;
    padding: 0 10px;
  }
  .screenfull {
    position: absolute;
    right: 90px;
    top: 16px;
    color: red;
  }
  .nav-right {
      height: 100%;
      float: right;
      .avatar-wrap{
        display: inline-block;
        margin-right: 20px;
        .user-avatar {
          width: 40px;
          height: 40px;
          border-radius: 10px;
          display: inline-block;
          vertical-align: middle;
        }
      }
      .logOut {
        font-size: 20px;
        display: inline-block;
        vertical-align: middle;
        color: #fff;
        cursor: pointer;
      }
  }
}
</style>

