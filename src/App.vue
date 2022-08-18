<template>
  <h1 class="font-bold text-3xl">LEVITICUS 27</h1>
  <h3 class="md:w-[25rem] p-3 mx-auto font-2xl my-5 text-bold">Base on leviticus 27, This app uses a person age to determine the amount to be paid as vow </h3>

  <div class="md:w-1/2 mx-auto p-3 md:p-10 bg-slate-800 ">
    <small class="text-yellow-300">input Age and Gender to get amount to be paid</small> <br>

    <div class="mt-5">
      <input id="age" v-model="age" class="p-4 outline-none  focus:ring-1 focus:ring-sky-500 shadow-xl rounded" type="number" >
   
   <select v-model="gender" class="p-4 ml-5 outline-none  focus:ring-1 focus:ring-sky-500 shadow-xl rounded">
      <option disabled value="">Select Gender</option>
     <option>Male</option>
     <option>Female</option>
  
</select>
    </div>

      
<br>
    <button @click="checkAge" class="bg-blue-500 py-4 px-10 mt-5 w-1/2 text-white text-lg shadow-xl">Check</button>

    <div v-if="visibility">
      <h2 class="text-white text-semibold text-lg my-5">Your vow is <span class="text-red-500">{{vow}}</span> shekels </h2>

    </div>
     <div v-if="invalid">
      <h2 class="text-white text-semibold text-lg my-5">Invalid selection </h2>
    </div>

  </div>

</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'


export default {
  name: 'App',
  data() {
    return {
       age:0,
       gender:'',
       vow:0,
       visibility:false,
       invalid:false
       
       }
  },
  
methods:{
  checkAge(){
    this.visibility=true;
    this.invalid=false;
    if(this.age<=4 && this.gender=="Male"){
      this.vow=5
    }else if(this.age<=4 && this.gender=="Female"){
      this.vow=3
  }else if(this.age<=19 && this.gender=="Male"){
      this.vow=20
    }else if(this.age<=19 && this.gender=="Female"){
       this.vow=10
  }else if(this.age<=59 && this.gender=="Male"){
      this.vow=50
    }else if(this.age<=59 && this.gender=="Female"){
       this.vow=30
  }else if(this.age>=60 && this.gender=="Male"){
      this.vow=15
    }else if(this.age>=60 && this.gender=="Female"){
       this.vow=10
  }else{
    this.invalid=true;
    this.visibility=false;
  }
  }



},
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
