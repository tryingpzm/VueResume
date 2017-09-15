<template>
  <div id="topbar">
    <p>VueResumer</p>
    <div class="logIn">
      <el-button type="primary">登录</el-button>
      <el-button>注册</el-button>
    </div>
  </div>
</template>

<style>
  #topbar{
    display:flex;
    justify-content:space-between;
    align-items: center;
    font-size:18px;
    margin:10px 10px;
  }
  #topbar>p{
    /*margin-left:10px;*/
  }


</style>
