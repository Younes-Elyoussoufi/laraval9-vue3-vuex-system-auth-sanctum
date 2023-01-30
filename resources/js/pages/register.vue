<template>
    <div class='row d-flex justify-content-center'>
      <div class='col-md-5'>
         <div class="text-center">
     
     <main class="form-signin">
      <p class="alert alert-danger" v-for='error in errors' :key="error"> 
        <span  v-for='err in error' :key="err"> 
          {{err}}
        </span>
        
      </p>

       <form @submit.prevent="register">
         
         <h1 class="h3 mb-3 fw-normal">register</h1>
     
         <div class="form-floating">
           <input type="text" class="form-control" v-model='form.name' placeholder="name@example.com">
           <label for="floatingInput">Full name</label>
         </div>

         <div class="form-floating">
           <input type="email" class="form-control" v-model='form.email' placeholder="name@example.com">
           <label for="floatingInput">Email address</label>
         </div>

         <div class="form-floating">
           <input type="password" class="form-control" v-model='form.password' placeholder="Password">
           <label for="floatingPassword">Password</label>
         </div>

         <div class="form-floating">
           <input type="password" class="form-control" v-model='form.c_password' placeholder="confirm Password">
           <label for="floatingPassword">confirm Password</label>
         </div>
     
         <div class="checkbox mb-3">
           <label>
             <input type="checkbox" value="remember-me"> Remember me
           </label>
         </div>
         <button class="w-100 btn btn-lg btn-primary" type="submit">register</button>
         <p class="mt-5 mb-3 text-muted">&copy; 2017–2021</p>
       </form>
     </main>
 
     </div>
      </div>
    </div>
 </template>

 
<script>
  import {reactive,ref } from 'vue'
  import {useRouter } from 'vue-router'
   export default{
 
     setup(){
       const router =useRouter();
       const form =reactive({
        name:'',
        email:'',
        password:'',
        c_password:''
      })
      const errors=ref([])
      const register = async ()=>{
        await axios.post('api/register',form).then(res=>{
          if(res.data.success){
            console.log(res.data)
            store.dispatch('setToken',res.data.data.token)
            router.push({name:'Dashboard'})
          }else{
            console.log(res.data.message)
          errors.value=res.data.message
          }
        
      } ).catch(err=>{
        errors.value=err.response.data.message
      }) 
    }
      return{
      form,
      register,
      errors
    }
    },
  
  }
</script>