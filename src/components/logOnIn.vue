<template>

  <div id="logOnIn" >
    <div id="logOnInContent">
      <h1>{{logOnIn}}</h1>
      <el-form :modeml="count">
          <el-input placeholder="username" v-model="count.username"></el-input>
        <div class="alarm">{{logonPrompt}}</div>
          <el-input placeholder="password" v-model="count.password"></el-input>
        <!--<div class="alarm" v-if="passwordError">登录密码错误</div>-->
        <div class="alarm">{{loginPrompt}}</div>
      </el-form>
    <div class="buttons">
      <el-button type="primary" @click="onSubmit">{{logOnIn}}</el-button>
      <el-button @click="notShowLog">取消</el-button>
    </div>
  </div>
  </div>
</template>

<script>
  export default{
      props:['logOnIn','count','initial'],
    methods:{
          onSubmit(){
              this.logonPrompt='';
              if(!this.initial){
               this.$emit("hasInitial")
               if(APP_ID) return;
                let APP_ID = 'BxivDc7nqWXFJiN5hTf2Yi2I-gzGzoHsz';
               let APP_KEY = 'z2Ucevf8n2jwIJkA7oyco7rS';

               AV.init({
                  appId: APP_ID,
                  appKey: APP_KEY
               });
              }
            //按钮被点击时
            if(this.logOnIn==="登录"){
              let query = new AV.Query('Count');
              query.equalTo('username', this.count.username);
              query.find().then(function(result){
                  if(result.length===0){
                      this.logonPrompt="此帐号尚未注册";
                      return;
                  }
                  let relPassword=result[0].attributes.password;
                  if(relPassword===this.count.password){
                      console.log("登录成功");
                    this.notShowLog();
                    this.logInSuccess();
                  }else{
//                      this.passwordError=true;
                        this.loginPrompt='登录密码错误';
                  }
              }.bind(this));
                return;
            }
            //下面是注册
            //先查询
            if(this.count.username.length<6||!/^[a-zA-Z]\w+$/.test(this.count.username)){
              this.logonPrompt="账户必须为7位以上的字母和数字的组合,必须字母开头";
              return;
            }else if(this.count.password.length<6||!/^[a-zA-Z]\w+$/.test(this.count.password)){
              this.loginPrompt="密码必须为6位以上字母、数字组合，必须字母开头";
              return;
            }
            let query = new AV.Query('Count');
            query.equalTo('username', this.count.username);
            query.find().then(function(result){
              if(result.length!==0){
                  this.logonPrompt="此用户名已被注册";
                  return;
              }
              this.notShowLog();
              this.logInSuccess();
              let countObject = AV.Object.extend('Count');
              let countObject1=new countObject;
              countObject1.set({"username":this.count.username,"password":this.count.password});
              countObject1.save().then(function() {
              });
            }.bind(this),function(){});
          },
          notShowLog(){
            this.$emit("notShowLog")
          },
          logInSuccess(){
              this.$emit("logInSuccess")
          }
    },
    data(){
          return {
              logonPrompt:'',
              loginPrompt:''
          }
    }
  }
</script>
<style>
  #logOnIn{
    position: absolute;
    left:0;
    top:0;
    width:100%;
    height:100%;
    background: url(https://i.loli.net/2017/10/02/59d2242955a77.jpg) no-repeat center;
    background-size: cover;
  }
  #logOnInContent{
    position: fixed;
    top:50%;
    left:50%;
    transform:translateX(-50%) translateY(-50%);
    width:300px;
    height:100px;
    z-index: 2;
    background-color: rgba(0,147,237,1);
  }
  #logOnInContent>h1{
    text-align: center;
    font-size:30px;
    color:#fff;
  }
  .buttons{
    padding:10px 0;
    display:flex;
    justify-content:space-around;
    background-color: rgba(0,147,237,1);
  }
  .alarm{
    color:red;
  }
</style>
