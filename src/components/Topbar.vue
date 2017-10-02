<template>
  <div id="topbar">
    <p>VueResumer</p>
    <div class="logIn">
      <el-button v-if="showLogOnIn" v-on:click="logIn" type="primary">登录</el-button>
      <!--<el-button><router-link to="/Xxx">注册</router-link></el-button>-->
      <span class="welcome" v-if="!showLogOnIn">欢迎你,{{count.username}}</span>
      <el-button v-if="showLogOnIn" v-on:click="logOn">注册</el-button>
      <el-button v-if="!showLogOnIn" v-on:click="logOut">退出登录</el-button>
      <!--<el-button v-if="!showLogOnIn" v-on:click="saveResume">保存简历</el-button>-->
      <el-button v-on:click="preview">预览</el-button>
    </div>
    <!--<router-view></router-view>-->
  </div>
</template>

<script>
  export default{
      props:['showLogOnIn','count'],
      methods:{
          preview(){
            this.$emit('preview')
          },
          logOn(){
            this.$emit('logOn')
          },
        logIn(){
              this.$emit('logIn')
        },
        logOut(){
            this.$emit('logOut')
        },
        saveResume(){
          this.$emit("saveResume")
        }
      }
  }
</script>
<style>
  #topbar{
    display:flex;
    justify-content:space-between;
    align-items: center;
    font-size:18px;
    padding:10px;
    box-shadow: 0 1px 3px rgba(0,0,0,0.12)
  }
  .welcome{
    margin-right:10px;
  }
</style>
