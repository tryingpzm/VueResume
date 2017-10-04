<template>
  <div id="preview">
    <section class="sidebar" v-if="showOrNot(resume.profile)">
      <i id="avatar"><img src="//i.loli.net/2017/10/04/59d453c782e5e.jpg" alt="头像"></i>

      <h1 class="name">{{resume.profile.name}}</h1>
      <p id="aimWork">求职意向：{{resume.profile.work}}</p>
      <hr>
      <h3 class="basicInformation">基本信息</h3>
      <p>
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-people"></use>
        </svg>
        {{resume.profile.sex}}|{{resume.profile.age}}
      </p>
      <p>
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-locationmaps"></use>
        </svg>
        {{resume.profile.city}}
      </p>
      <section v-if="showOrNot(resume.contacts)">
        <p>
          <svg class="icon" aria-hidden="true">
            <use xlink:href="#icon-qq"></use>
          </svg>
          qq:{{resume.contacts.qq}}
        </p>
        <p>
          <svg class="icon" aria-hidden="true">
            <use xlink:href="#icon-wechaticon"></use>
          </svg>
          微信:{{resume.contacts.wechat}}
        </p>
        <p>
          <svg class="icon" aria-hidden="true">
            <use xlink:href="#icon-email"></use>
          </svg>
          邮箱: {{resume.contacts.email}}
        </p>
        <p>
          <svg class="icon" aria-hidden="true">
            <use xlink:href="#icon-phone1"></use>
          </svg>
          手机: {{resume.contacts.phone}}
        </p>
        <hr>
      </section>
      <!--自我评价 -->
      <h3>自我评价</h3>
      <p>
        {{resume.profile.assignment}}
      </p>
    </section>
    <section class="main">
      <section v-if="showOrNot(resume.studyHistory)">
        <h3>
          <svg class="icon" aria-hidden="true">
            <use xlink:href="#icon-you"></use>
          </svg>
          教育背景
        </h3>
        <ul>
          <li class="spanWrap" v-for="study in resume.studyHistory">
            <span>{{study.duration}}</span><span>{{study.school}}</span><span>{{study.degree}}</span>
          </li>
        </ul>
        <hr>
      </section>
      <!--工作经历 -->
      <section v-if="showOrNot(resume.workHistory)">
        <h3>
          <svg class="icon" aria-hidden="true">
            <use xlink:href="#icon-you"></use>
          </svg>
          工作经历
        </h3>
        <ul>
          <li class="spanWrap" v-for="work in resume.workHistory">
            <span>{{work.duration}} </span><span>{{work.company}}</span><span>{{work.content}}</span>
          </li>
        </ul>
        <hr>
      </section>
      <!--项目经历 -->
      <section v-if="showOrNot(resume.projects)">
        <h3>
          <svg class="icon" aria-hidden="true">
            <use xlink:href="#icon-you"></use>
          </svg>
          项目经历
        </h3>
        <ul>
          <li class="spanWrap" v-for="project in resume.projects">
            <h4>{{project.name}}</h4><span>{{project.content}}</span>
          </li>
        </ul>
        <hr>
      </section>
      <section v-if="showOrNot(resume.profile.skills)">
        <h3>
          <svg class="icon" aria-hidden="true">
            <use xlink:href="#icon-you"></use>
          </svg>
          个人技能
        </h3>
        <p class="spanWrap"><span>{{resume.profile.skills}}</span></p>
        <hr>
      </section>
      <section v-if="showOrNot(resume.awards)">
        <ul>
          <li v-for="award in resume.awards">
            <h3>
              {{award.content}}
            </h3>
          </li>
        </ul>
        <hr>
      </section>
    </section>
  </div>
</template>

<script>
  export default{
    props: ["resume"],
    methods: {
      showOrNot(arrayOrObject){
        let flag = false;
        if (arrayOrObject instanceof Array) {
          outer:
            for (let i = 0; i < arrayOrObject.length; i++) {
              let keys = Object.keys(arrayOrObject[i]);
              for (let index in keys) {
                if (arrayOrObject[i][keys[index]]) {
                  flag = true;
                  break outer;
                }
              }
            }
        } else {
          for (let key in arrayOrObject) {
            if (arrayOrObject[key]) {
              flag = true;
              break;
            }
          }
        }
        return flag;
      }
    },
  }
</script>

<style>
  #preview {
    flex: 1;
    margin: 16px auto;
    box-shadow: 0 0 3px rgba(0, 0, 0, 0.32);
    border-radius: 4px;
    display: flex;
    flex-direction:row;
    max-width: 500px;
    overflow: auto;
  }

  hr {
    margin: 8px 0;
  }

  #preview .sidebar {
    background-color: #201C35;
    max-width: 160px;
    color: #fff;
    padding: 20px;
    min-height:100vh;
  }
  #preview .sidebar #avatar{
    width:80%;
    margin:0 auto;
  }
  #preview .sidebar #avatar img{
    width:100%;
    border-radius:50%;
  }
  #preview .sidebar .name {
    font-weight: normal;
    font-size: 24px;
  }

  #preview .sidebar h3{
    padding: 16px 0;
  }
  #preview .sidebar .icon{
    fill:#fff;
  }
  #preview .sidebar p {
    font-size: 12px;
    padding: 8px 0;
  }

  #preview .main {
    flex-grow: 1;
    color:#000;
    padding-left:10px;
  }
  #preview .main h3{
    padding:16px 0;
  }
  #preview .main h4{
    padding-bottom:8px;
  }
  #preview .main .spanWrap{
    padding:8px 0;
  }
  #preview .main .spanWrap span{
    margin-right:16px;
  }
  #preview .main .spanWrap span:last-child{
    margin-right:0;
  }
</style>
