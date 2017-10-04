<template>
  <div id="ProfileEdit">
    <h2>个人信息</h2>
    <el-form>
      <el-form-item label="名称"></el-form-item>
      <el-input v-model="profile.name"></el-input>
      <el-form-item label="性别"></el-form-item>
      <el-input v-model="profile.sex"></el-input>
      <el-form-item label="年龄"></el-form-item>
      <el-input v-model="profile.age"></el-input>
      <el-form-item label="意向职位"></el-form-item>
      <el-input v-model="profile.work"></el-input>
      <el-form-item label="意向城市"></el-form-item>
      <el-input v-model="profile.city"></el-input>
      <el-form-item label="相关技能"></el-form-item>
      <el-input v-model="profile.skills"></el-input>
      <el-form-item label="自我评价"></el-form-item>
      <el-input v-model="profile.assignment"></el-input>

    </el-form>
  </div>
</template>

<script>
  export default{
      //允许一个profile的变量
      props:['profile']
  }
</script>
