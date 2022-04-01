<template>
<div>
  <Navbarnew />
  <div class="registerPage">
    <div class="container">
      <div class="row">
        <div class="col-sm-4"></div>
        <div class="col-sm-4">
          <div v-show="message" class="text-center">
            {{message}}
          </div>

          <form class="mt-4">
            <div class="a-box a-spacing-extra-large">
              <div class="a-box-inner">
                <h1 class="a-spacing-small">Signin to account</h1>

                <!-- Email -->
                <div class="a-row a-spacing-base">
                  <label for="ap_customer_name" class="a-form-lable">Email</label>
                  <input type="email"
                  v-model="email"
                  id="ap_customer_name"
                  class="a-input-text form-control auth-autofocus auth-required-field auth-contact-verification-request-info" />
                </div>

                <!-- Password -->
                <div class="a-row a-spacing-base">
                  <label for="ap_customer_name" class="a-form-lable">Password</label>
                  <input type="password"
                  v-model="password"
                  id="ap_customer_name"
                  class="a-input-text form-control auth-autofocus auth-required-field auth-contact-verification-request-info" />
                  <div class="a-alert-container">
                    <div class="a-alert-content">Password must be at least 6 Character long </div>
                  </div>
                </div>
                <!-- button -->
                <div class="a-row a-spacing-extra-large mb-4">
                  <span class="a-button-primary">
                    <span class="a-button-inner">
                      <span @click="onLogin" class="a-button-text">Signin</span>
                    </span>
                  </span>
                  <div class="a-row a-spacing-top-medium a-size-small">
                    <b>
                      After login, you agree to our
                       <router-link to="/termsandconditions">conditions of use</router-link> and 
                       <router-link to="/privacypolicy">Privacy Notice</router-link>
                    </b>
                  </div>
                </div>
                <hr />
                <div class="a-row">
                  <b>
                    Don't have a account?
                    <nuxt-link to="/signup" class="a-link-emphasis">Register</nuxt-link>
                  </b>
                </div>  
              </div>
            </div>
          </form>
        </div>
      </div>
      
    </div>
  </div>
<Footernew />
  </div>
</template>

<script>

export default {
  middleware: 'auth',
  auth: 'guest',
   head() {
    return {
      title: "Login"
    };
  },
 data(){
   return{
     email:'',
     password:'',
     message: ''
   }
 },
 methods: {
   async onLogin(){
    //  console.log("called post method")
     try{
       let data = {
         email: this.email,
         password: this.password
       }
       let response = await this.$axios.$post('https://brahmapuri-server.herokuapp.com/api/auth/login', data)
       if(response.success){
         localStorage.setItem('brahmapuriToken', response.token)
         this.$cookies.set('brahmapuriToken', response.token)
         this.$router.push('/')
        //  window.location.reload(true)
       } else {
         this.message = "Enter email or password correctly"
             return
       }
        //  this.$auth.loginWith('local',{
        //    data:{
        //      email: this.email,
        //      password: this.password
        //    }
        //  }).then(response =>{
        //    console.log("login response", response)
          //  if(response.data.success){
          //    this.$cookies.set('brahmapuriToken', response.data.token)
          //    window.location.reload(true)
          //    this.$router.push('/')
          //  } 
          //  if(!response.success) {
          //    this.message = "Enter email or password correctly"
          //    console.log("wrong password")
          //    return
          //  }
         //})
        //  this.$forceUpdate();
     } catch(err){
       console.log(err)
     }
   }
 }
}
</script>
