<template>
  <div id="app">
    <Topbar class="topbar"/>
    <main>
        <Edit class="edit"/>
        <Preview class="preview"/>
    </main>
  </div>
</template>

<script>
import Topbar from './components/Topbar'
import Edit from './components/Edit'
import Preview from './components/Preview'

export default {
  name: 'app',
  components: {Topbar,Edit,Preview}
}
</script>

<style>
  *{
  font-family: "Arial","Microsoft
   YaHei","黑体","宋体",sans-serif;
  }
  #app{
  border:1px solid;
  display:flex;
  height:100vh;
  flex-direction:column;
  }
  .topbar{

  }
  main{
  flex:1;
  border:1px solid;
  display:flex;
  }
  main .edit{
  width:300px;
  }
  main .preview{
   flex:1;
  }

</style>
