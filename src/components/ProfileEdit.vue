<template>
  <div id="ProfileEdit">
    <h2>个人信息</h2>
    <el-form>
      <el-form-item label="名称"></el-form-item>
      <el-input v-model="profile.name"></el-input>
      <el-form-item label="城市"></el-form-item>
      <el-input v-model="profile.city"></el-input>
      <el-form-item label="出生年月"></el-form-item>
      <el-input v-model="profile.birth"></el-input>
    </el-form>
  </div>
</template>

<script>
  export default{
      //允许一个profile的变量
      props:['profile']
  }
</script>
