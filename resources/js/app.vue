<template>
    
    <div>
        <div>
            <nav class="navbar navbar-expand-md navbar-dark bg-dark mb-4">
  <div class="container-fluid">
   
    <router-link class="navbar-brand" aria-current="page"  :to='{name:"Home"}'>
      Home 
    </router-link>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarCollapse" aria-controls="navbarCollapse" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarCollapse">
      <ul class="navbar-nav me-auto mb-2 mb-md-0">
      
        <li class="nav-item">
       
          <router-link class="nav-link" :to='{name:"Login"}'
          v-if="$store.getters.getToken==0" >Login</router-link>
        </li>
        <li class="nav-item">
         
          <router-link class="nav-link" :to='{name:"Register"}' 
          v-if="$store.getters.getToken==0" >Register</router-link>
        </li>
        <li class="nav-item">
         
         <router-link class="nav-link" :to='{name:"Dashboard"}' 
         v-if="$store.getters.getToken!=0" >Dashboard</router-link>
       </li>
      </ul>
     
    </div>
  </div>
</nav>

          
        </div>
        <router-view></router-view>
    </div>

</template>


<script>
  import {useRouter } from 'vue-router'
  import {useStore } from 'vuex'
  
  export default{

    setup(){
      const router =useRouter();
      const store =useStore();

      return{
      

    }
    },
  
  }
</script>