<template>
      
    <div class=' d-flex justify-content-center'>
       <div>dashboard</div> <br>
       <button class="btn btn-dark" @click="logout">logout</button>
    </div>
 </template>
 
 <script>
   import {useRouter } from 'vue-router'
   import {useStore } from 'vuex'
   
   export default{
 
     setup(){
       const router =useRouter();
       const store =useStore();

       const logout =  ()=>{
        store.dispatch('removeToken')
        router.push('/')
       }
       return{
        logout,

     }
     },
   
   }
 </script>