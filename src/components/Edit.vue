<template>
  <div id="edit">
    <div class="nav">
      <ol>
        <li v-for="i in [0,1,2,3,4,5]" v-bind:class="{active:currentTab===i}" v-on:click="currentTab=i">
          <svg class="icon">
            <use v-bind:xlink:href="'#icon-'+icons[i]"></use>
          </svg>
        </li>
      </ol>
    </div>
    <ol class="content">
      <li v-bind:class="{active:currentTab===0}">
        <ProfileEdit v-bind:profile="resume.profile"></ProfileEdit>
      </li>
      <li v-bind:class="{active:currentTab===1}">
        <ArrayEdit v-bind:items="resume.workHistory" v-bind:head="'工作经历'" v-bind:labels="{company:'公司',content:'工作内容',duration:'时间段'}"></ArrayEdit>
      </li>
      <li v-bind:class="{active:currentTab===2}">
        <ArrayEdit v-bind:items="resume.studyHistory" v-bind:head="'学习经历'" v-bind:labels="{school:'学校',duration:'持续时间',degree:'学位'}"></ArrayEdit>
      </li>
      <li v-bind:class="{active:currentTab===3}">
        <ArrayEdit v-bind:items="resume.projects" v-bind:head="'项目'" v-bind:labels="{name:'项目名称',content:'项目内容'}"></ArrayEdit>
      </li>
      <li v-bind:class="{active:currentTab===4}">
        <ArrayEdit v-bind:items="resume.awards" v-bind:head="'获奖情况'" v-bind:labels="{content:'奖励详情'}"></ArrayEdit>
      </li>
      <li v-bind:class="{active:currentTab===5}">
        <ContactEdit v-bind:contacts="resume.contacts"></ContactEdit>
      </li>
    </ol>
  </div>
</template>

<script>
  import ProfileEdit from './ProfileEdit.vue'
  import ArrayEdit from './ArrayEdit'
  import ContactEdit from './ContactEdit.vue'
  export default{
    components: {ProfileEdit,ArrayEdit,ContactEdit},
    props:["resume"],
    data(){
      return {
        currentTab: 0,
        icons: ["shenfenzheng", "gongzuo", "book", "xiangmu1", "jiangbei", "phone"],

      }
    },
  }
</script>
<style lang="scss">
  #edit {
    width: 400px;
    overflow: hidden;
    margin: 16px 8px 16px 16px;
    box-shadow: 0 0 3px rgba(0, 0, 0, 0.32);
    border-radius: 4px;
    display: flex;
  }

  #edit .nav {
    background-color: #000;
  }

  #edit .nav li {
    padding: 16px;
  }

  #edit .nav li.active {
    background-color: #fff;

  svg {
    fill: black;
  }

  }
  #edit .nav svg {
    fill: #fff;
    width: 24px;
    height: 24px;
    /*border:1px solid red;*/
  }

  #edit .content {
    flex: 1;
    overflow: auto;
  }

  #edit .content li {
    display: none;
    padding: 16px;
  }

  #edit .content li.active {
    display: block;
  }

  #edit .content li div {
    position: relative;
  }

  #edit .content li div i.el-icon-circle-close {
    position: absolute;
    top: 8px;
    right: 8px;
  }

  #edit .content li .addButton {
    margin-top: 20px;
  }

  #edit .content li hr {
    margin-top: 20px;

  }
</style>
