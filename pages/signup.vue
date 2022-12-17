<template>
<div>
  <Navbarnew />
  <div class="registerPage">
    <div class="container">
      <div class="row">
        <div class="col-sm-4"></div>
        <div class="col-sm-4">

          <form class="mt-4">
            <div class="a-box a-spacing-extra-large">
              <div class="a-box-inner">
                <h1 class="a-spacing-small">Create account</h1>
                <!-- your name -->
                <div class="a-row a-spacing-base">
                  <label for="ap_customer_name" class="a-form-lable">Your name</label>
                  <input type="text"
                  v-model="name"
                  id="ap_customer_name"
                  class="a-input-text form-control auth-autofocus auth-required-field auth-contact-verification-request-info" />
                </div>

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
                      <span @click="onSignup" class="a-button-text">Create your Account</span>
                    </span>
                  </span>
                  <div class="a-row a-spacing-top-medium a-size-small">
                    <b>
                      By creating an account, you agree to our
                       <router-link to="/termsandconditions">conditions of use</router-link> and 
                       <router-link to="/privacypolicy">Privacy Notice</router-link>
                    </b>
                  </div>
                </div>
                <hr />
                <div class="a-row">
                  <b>
                    Already have an account?
                    <nuxt-link to="/loginnew" class="a-link-emphasis">Sign in</nuxt-link>
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
   head() {
    return {
      title: "Signup with Us"
    };
  },
 data(){
   return{
     name:'',
     email:'',
     password:''
   }
 },
 methods: {
   async onSignup(){
     if(!this.name || !this.email || !this.password){
       alert("Please enter all the fields to register")
       return
     }
     try{
       let data = {
         name: this.name,
         email: this.email,
         password: this.password
       }
       let response = await this.$axios.$post('https://rose-important-hedgehog.cyclic.app/api/auth/signup', data)
       if(response.success){
        localStorage.setItem('brahmapuriToken', response.token)
         this.$cookies.set('brahmapuriToken', response.token)
         this.$auth.loginWith('local',{
           data:{
             email: this.email,
             password: this.password
           }
         })
         this.$router.push('/')
       }
       if(!response.success){
         alert(response.message)
       }
     } catch(err){
       console.log(err)
     }
   }
 }
}
</script>
