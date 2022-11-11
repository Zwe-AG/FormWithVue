<template>
  <form @submit.prevent="submit">
    <h1 style="text-align:center">Sign Up</h1>
    <div>
      <label for="">Email</label>
      <input type="email" v-model="email">
    </div>
    <div>
      <label for="">Password</label>
      <input type="password" v-model="password">
    </div>
    <p v-if="errorMsg" class="error">{{errorMsg}}</p>
    <div>
      <label for="">Experiences</label> <br>
      <input type="checkbox" value="oneyear" v-model="experiences">
      <label for="" style="margin-right:10px">1 years</label>
      <input type="checkbox" value="twoyear" v-model="experiences">
      <label for="" style="margin-right:10px">2 years</label>
      <input type="checkbox" value="threeyear" v-model="experiences">
      <label for="">3years</label>
    </div>
    <div>
        <label for="">Skills</label>
        <input type="text" @keyup.alt="addSkill" v-model="skill">
    </div>
    <div v-for="skill in skills" :key="skill">
        <p>{{skill}} <span class="cross" @click="deleteSkill(skill)">&#x2716;</span>
        </p>
      </div>
      <div>
          <input type="checkbox" v-model="accept">
          <label for="">Accept Terms and condition</label>
      </div>
      <div class="align">
        <button class="create">Create Account</button>
      </div>
  </form>
  <p>email - {{email}}</p>
  <p>password - {{password}}</p>
  <p>experiences - {{experiences}}</p>
  <p>accept - {{accept}}</p>
</template>

<script>
export default {
data() {
  return {
    email : "",
    password : "",
    experiences : [],
    accept : false,
    skill : "",
    skills :[],
    errorMsg :""

  }
},
methods:{
  addSkill(e){
    if(e.key==="," && this.skill){
      this.skills = this.skills.push(this.skill);
      this.skill="";
    }
  },
  deleteSkill(skill){
    this.skills = this.skills.filter((skill)=>{
       return skill !== skill
    })
  },
  submit(){
    if(this.password.length<8){
          this.errorMsg="Password Must me at least 8 characters" 
        }
  }
}
}
</script>

<style>
 form {
        max-width: 420px;
        margin: 30px auto;
        background: white;
        text-align: left;
        padding: 40px;
        border-radius: 10px;
      }
      label {
        color: #aaa;
        display: inline-block;
        margin: 25px 0 15px;
        font-size: 0.6em;
        text-transform: uppercase;
        letter-spacing: 1px;
        font-weight: bold;
      }
      input,select {
        display: block;
        padding: 10px 6px;
        width: 100%;
        box-sizing: border-box;
        border: none;
        border-bottom: 1px solid #ddd;
        color: #555;
      }
      input[type="checkbox"] {
        display: inline-block;
        width: 16px;
        margin: 0 10px 0 0;
        position: relative;
        top: 2px;
      }
      .cross{
        cursor: pointer;
        color:red
      }
      
      .create{
        background-color: royalblue;
        padding:10px 20px;
        color: white;
        border-radius: 5px;
        border:none
      }
      .align{
        text-align: center;
        margin-top:10px
      }
      .error{
        color:crimson;
      }
</style>
