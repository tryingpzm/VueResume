<template>
  <div id="preview">
    <h1>{{profile.name}}</h1>
    <p>{{profile.city}}|{{profile.birth}}</p>
  </div>
</template>

<script>
  export default{
      props:["profile","workHistory","studyHistory","projects","awards","contacts"]
  }
</script>

<style>
  #preview{
       /*border:1px solid;*/
       flex:1;
       margin:16px 16px 16px 8px;
       box-shadow: 0 0 3px rgba(0,0,0,0.32);
       border-radius:4px;
     }
</style>
