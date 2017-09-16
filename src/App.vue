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
  #app{
  border:1px solid;
  display:flex;
  height:100vh;
  flex-direction:column;
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
