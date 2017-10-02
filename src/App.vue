<template>
  <div id="app" v-bind:class="{previewClass}">
    <Topbar id="topbar" v-on:saveResume="saveResume" v-on:logOut="logOut"  v-on:preview="preview" v-on:logOn="logOn" v-on:logIn="logIn" v-bind:showLogOnIn="showLogOnIn" v-bind:count="count"></Topbar>
    <main>
        <Edit v-bind:resume="resume" id="edit"/>
        <Preview v-bind:resume="resume" id="preview"/>
    </main>
    <Xxx id="Xxx" v-bind:initial="initial" v-if="showLog" v-on:hasInitial="hasInitial" v-on:logInSuccess="logInSuccess" v-on:notShowLog="notShowLog" v-bind:logOnIn="logOnIn" v-bind:showLog="showLog" v-bind:count="count"></Xxx>
    <el-button id="outPreview" v-on:click="outPreview">退出预览</el-button>
  </div>
</template>

<script>
import Topbar from './components/Topbar'
import Edit from './components/Edit'
import Preview from './components/Preview'
import Xxx from './components/Xxx'
export default {
  name: 'app',
  components: {Topbar,Edit,Preview,Xxx},
  data(){
      return {
          resume:{
            profile: {
              name: "",
              city: "",
              birth: ""
            },
            workHistory: [
              {company: "", content: ""}
            ],
            studyHistory:[
              {school:"",duration:"",degree:""}
            ],
            projects:[
              {name:'',content:''}
            ],
            awards:[
              {content:''}
            ],
            contacts:{
                qq:'',wechat:'',email:'',phone:''
            }

          },
        count:{
          username:"",
          password:""
        },
        previewClass:false,
        showLog:false,
        logOnIn:"xx",
        showLogOnIn:true,
        initial:false,
      }
  },
  methods:{
      preview(){
        this.previewClass=true;
      },
      outPreview(){
          this.previewClass=false;
      },
      logOn(){
        this.showLog=true;
        this.logOnIn="注册"
      },
    logIn(){
      this.showLog=true;
      this.logOnIn="登录"
    },
    notShowLog(){
          this.showLog=false;
    },
    logInSuccess(){
        this.showLogOnIn=false;
    },
    hasInitial(){
        this.initial=true;
    },
    logOut(){
        this.count={username:'',password:''},
          this.showLogOnIn=true;
        this.showLog=false;
    },
    saveResume(){
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

    }
  }
}
</script>

<style lang="scss">
  #app{
  display:flex;
  height:100vh;
  flex-direction:column;
    position: relative;
  }
  #app.previewClass #topbar{
    display:none;
  }
  #app.previewClass #edit{
    display:none
  }
  #app.previewClass #preview{
    max-width:800px;
    margin:24px auto;
  }
  #app.previewClass #outPreview{
    display:block;
    position: fixed;
    top:0;
    right:0;
  }
  #app #outPreview{
    display:none;
  }
  #app main{
  flex:1;
  display:flex;
  }
  .icon {
    width: 1em; height: 1em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
  }

</style>
