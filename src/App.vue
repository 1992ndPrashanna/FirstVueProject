<template>
  <div id="app">
    {{ user.username }} - {{fullName}} <br>
    <strong>
      Followers :
    </strong>
    {{followers}} <br>
    
  </div>
   <button class="follow" @click="followUser">Follow</button> 
</template>

<script>

export default {
  name: 'App',
  data(){ 
    return{
      followers:0,
      user:{
        id:1,
        username:'TheAxeMonger',
        firstName:'Prashanna',
        lastName:'Bhandari',
        email:'prashanna1992@outlook.com',
        isAdmin:true
      }
    }
  },
  computed:{
    fullName(){
      return this.user.firstName +" "+ this.user.lastName
    }
  },
  methods:{
    followUser(){
      this.followers++
    }
  },
  mounted(){
    this.followUser();
  },
  watch:{
    followers(newFollowerCount,oldFollowerCount){
      if(oldFollowerCount<newFollowerCount){
        console.log(`${this.user.username} has gained a follower!`);
      }
    }
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display:flex;
  flex-direction:column;
  text-align: center;
}
</style>
