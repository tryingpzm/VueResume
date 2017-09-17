<template>
  <div id="preview">
    <section v-if="showOrNot(resume.profile)">
      <h1>{{resume.profile.name}}</h1>
      <p>{{resume.profile.city}}|{{resume.profile.birth}}</p>
      <hr>
    </section>
    <section v-if="showOrNot(resume.studyHistory)">
      <ul>
        <li v-for="study in resume.studyHistory">
          <h2>
            {{study.school}}
          </h2>
          {{study.duration}}|{{study.degree}}
        </li>
      </ul>
      <hr>
    </section>
    <section v-if="showOrNot(resume.projects)">
      <ul>
        <li v-for="project in resume.projects">
          <h2>
            {{project.name}}
          </h2>
          {{project.content}}
        </li>
      </ul>
      <hr>
    </section>
    <section v-if="showOrNot(resume.workHistory)">
      <ul>
        <li v-for="work in resume.workHistory">
          <h2>
            {{work.company}}
          </h2>
          {{work.content}}
        </li>
      </ul>
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
    <section v-if="showOrNot(resume.contacts)">
          <p>qq:{{resume.contacts.qq}}</p>
          <p>微信:{{resume.contacts.wechat}}</p>
          <p>邮箱:{{resume.contacts.email}}</p>
          <p>手机:{{resume.contacts.phone}}</p>
      <hr>
    </section>
  </div>
</template>

<script>
  export default{
      props:["resume"],
      methods:{
          showOrNot(arrayOrObject){
            let flag=false;
            if(arrayOrObject instanceof Array){
              outer:
                for(let i=0;i<arrayOrObject.length;i++){
                  let keys=Object.keys(arrayOrObject[i]);
                  for(let index in keys){
                    if(arrayOrObject[i][keys[index]]){
                      flag=true;
                      break outer;
                    }
                  }
                }
            }else{
                for(let key in arrayOrObject){
                    if(arrayOrObject[key]){
                        flag=true;
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
  #preview{
       /*border:1px solid;*/
       flex:1;
       margin:16px 16px 16px 8px;
       box-shadow: 0 0 3px rgba(0,0,0,0.32);
       border-radius:4px;
     }
  hr{
    margin-top:20px;
  }
</style>
