<template>
    <div>
        <Navbarnew />
        <div class="container">
         <div>
                <h1>Login</h1>
        <form>
        <div class="row">
            <label for="email">Email</label>
            <input  v-model="email" type="email" name="email" autocomplete="on" placeholder="email@example.com">
        </div>
        <div class="row">
            <label for="password">Password</label>
            <input v-model="password" type="password" name="password">
        </div>
        <button @click="onLogin">Login</button>
        <p style="margin-top:10px"> Don't have a account?
                    <nuxt-link to="/signupnew" class="a-link-emphasis">Register</nuxt-link></p>
        </form>
         </div>
         <p>{{message}}</p>
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
     event.preventDefault()
    //  console.log("called post method")
     try{
       let data = {
         email: this.email,
         password: this.password
       }
       let response = await this.$axios.$post('https://rose-important-hedgehog.cyclic.app/api/auth/login', data)
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

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Open+Sans&display=swap');

body {
  font-family: 'Open Sans', sans-serif;
  background: #f9faff;
  color: #3a3c47;
  line-height: 1.6;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 0;
  padding: 0;
}
.container {
  display: flex;
  justify-content: center;
  margin-bottom: 60px;
}

h1 {
  margin-top: 48px;
  text-align: center;
}

form {
  background: #fff;
  max-width: 380px;
  width: 100%;
  padding: 58px 44px;
  border: 1px solid #e1e2f0;
  border-radius: 4px;
  box-shadow: 0 0 5px 0 rgba(42, 45, 48, 0.12);
  transition: all 0.3s ease;
}

.row {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

.row label {
  font-size: 13px;
  color: #8086a9;
}

.row input {
  flex: 1;
  padding: 13px;
  border: 1px solid #d6d8e6;
  border-radius: 4px;
  font-size: 16px;
  transition: all 0.2s ease-out;
}

.row input:focus {
  outline: none;
  box-shadow: inset 2px 2px 5px 0 rgba(42, 45, 48, 0.12);
}

.row input::placeholder {
  color: #C8CDDF;
}

button {
  width: 100%;
  padding: 12px;
  font-size: 18px;
  background: #4C8D2B;
  color: #fff;
  border: none;
  border-radius: 100px;
  cursor: pointer;
  font-family: 'Open Sans', sans-serif;
  margin-top: 15px;
  transition: background 0.2s ease-out;
}

button:hover {
  background: #55D3AC;
}
a {
  text-decoration: none;
}

@media(max-width: 458px) {
  
  body {
    margin: 0 18px;
  }
  
  form {
    background: #f9faff;
    border: none;
    box-shadow: none;
    /* padding: 20px 0; */
  }

}
</style>