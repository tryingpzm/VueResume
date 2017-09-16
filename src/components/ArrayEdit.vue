<template>
  <div>
    <h2>{{head}}</h2>
    <el-form>
      <div v-for="(item,index) in myItems">
        <div v-for="key in keys">
          <el-form-item  v-bind:label="labels[key]"></el-form-item>
          <el-input v-model="item[key]"></el-input>
        </div>
        <i class="el-icon-circle-close" v-on:click="removeItem(index)"></i>
        <hr>
      </div>
      <el-button class="addButton" type="primary" v-on:click="addItem">添加</el-button>
    </el-form>
  </div>
</template>

<script>
  export default{
      props:['head',"items","labels"],
      data(){
          return {
            myItems:this.items
          }
      },
      computed: {
        keys(){
          return Object.keys(this.items[0])
        }
      },
    methods:{
      addItem(){

        let obj={};
        this.keys.forEach(function(key){
          obj.key='';
        });
        this.myItems.push(obj)
      },
      removeItem(index){
          if(this.myItems.length===1){
            alert("至少有一项")
            return;
          }
          this.myItems.splice(index,1)
      }
    },
  }
</script>
