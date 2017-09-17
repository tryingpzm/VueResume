<template>
  <div id="app"  v-bind:class="{previewClass:previewClass}">
    <Topbar id="topbar"  v-on:preview="preview"/>
    <main>
        <Edit v-bind:resume="resume" id="edit"/>
        <Preview v-bind:resume="resume" id="preview"/>
    </main>
    <el-button id="outPreview" v-on:click="outPreview">退出预览</el-button>
  </div>
</template>

<script>
import Topbar from './components/Topbar'
import Edit from './components/Edit'
import Preview from './components/Preview'

export default {
  name: 'app',
  components: {Topbar,Edit,Preview},
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
        previewClass:false
      }
  },
  methods:{
      preview(){
        this.previewClass=true;
      },
      outPreview(){
          this.previewClass=false;
      }
  }
}
</script>

<style lang="scss">
  #app{
  border:1px solid;
  display:flex;
  height:100vh;
  flex-direction:column;
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
  main{
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
