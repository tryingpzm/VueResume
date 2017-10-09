<template>
  <div id="app" v-bind:class="{previewClass}">
    <Topbar id="topbar" v-on:saveResume="saveResume" v-on:logOut="logOut"  v-on:preview="preview" v-on:logOn="logOn" v-on:logIn="logIn" v-bind:showLogOnIn="showLogOnIn" v-bind:count="count"></Topbar>
    <main>
        <Edit v-bind:resume="resume" id="edit"/>
        <Preview v-bind:resume="resume" id="preview"/>
    </main>
    <logOnIn id="logOnIn" v-bind:initial="initial" v-if="showLog" v-on:hasInitial="hasInitial" v-on:logInSuccess="logInSuccess" v-on:notShowLog="notShowLog" v-bind:logOnIn="logOnIn" v-bind:showLog="showLog" v-bind:count="count"></logOnIn>
    <el-button id="outPreview" v-on:click="outPreview">退出预览</el-button>
  </div>
</template>

<script>
import Topbar from './components/Topbar'
import Edit from './components/Edit'
import Preview from './components/Preview'
import logOnIn from './components/logOnIn'
export default {
  name: 'app',
  components: {Topbar,Edit,Preview,logOnIn},
  data(){
      return {
          resume:{
            profile: {
              name: "彭志明",
              sex:"男",
              work:"前端工程师",
              city: "广东省广州市",
              age: "23",
              assignment:"熟练掌握HTML5、CSS3、JavaScript,了解jQuery库、Vue.js框架，乐于学习新技术",
              skills:"HTML5 CSS3 JavaScript jQuery Vue"
            },
            workHistory: [
              {company: "广东省水利水电第三工程局", content: "测量员",duration:"2016.9-2017.5"}
            ],
            studyHistory:[
              {school:"武汉大学",duration:"2012.9-2016.6",degree:"学士学位"}
            ],
            projects:[
              {name:'英雄联盟官网仿站',content:'html+css+原生javascript'},
              {name:'网易云音乐网页版仿',content:'预加载+函数节流+jQuery+BOM+leancloud(数据库)+requirejs'}
            ],
            awards:[
              {content:"国家乙等奖学金"}
            ],
            contacts:{
                qq:'717864916',wechat:'a717864916',email:'717864916@qq.com',phone:'18664366385'
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
    /*max-width:800px;*/
    margin:0 auto;
    overflow:auto;
  }
  #app.previewClass #preview #contentWrap{

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
