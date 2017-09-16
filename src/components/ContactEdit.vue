<template>
  <div id="ContactEdit">
    <h2>联系方式</h2>
    <el-form>
      <el-form-item label="QQ"></el-form-item>
      <el-input v-model="contacts.qq"></el-input>
      <el-form-item label="微信"></el-form-item>
      <el-input v-model="contacts.wechat"></el-input>
      <el-form-item label="邮箱"></el-form-item>
      <el-input v-model="contacts.email"></el-input>
      <el-form-item label="电话"></el-form-item>
      <el-input v-model="contacts.phone"></el-input>
    </el-form>
  </div>
</template>

<script>
  export default{
    props:['contacts']
  }
</script>
