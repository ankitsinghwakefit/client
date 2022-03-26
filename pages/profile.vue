<template>
<div>
  <Navbarnew />
  <main>
    <div class="container-fluid c-section">
      <div class="row">
        <div class="col-sm-3"></div>
        <div class="col-sm-6">
          <div class="a-spacing-top-medium"></div>
          <h2>Profile Page</h2>
          <form>
            <!-- Name -->
            <div class="a-spacing-top-medium">
              <label>Name</label>
              <input class="a-input-text" style="width: 100%" v-model="name">
            </div>

            <!-- Email -->
            <div class="a-spacing-top-medium">
              <label>Email</label>
              <input class="a-input-text" style="width: 100%" v-model="email">
            </div>

            <!-- Password -->
            <!-- <div class="a-spacing-top-medium">
              <label>Password</label>
              <input class="a-input-text" style="width: 100%" v-model="password">
            </div> -->

            <hr />
            <div class="a-spacing-top-large">
              <span class="a-button-register">
                <!-- <span class="a-button-inner">
                  <span class="a-button-text" @click="onUpdateProfile">Update Profile</span>
                </span> -->
              </span>
            </div>
          </form>
          <br/>
        </div>
        <div class="col-sm-3"></div>
      </div>
    </div>
  </main>
  <Footernew />
  </div>
</template>

<script>
export default {
   head() {
    return {
      title: "Your Profile"
    };
  },
  data(){
    return{
      name: '',
      email: '',
      password: ''
    }
  },
   created () {
    if(this.$cookies.get('brahmapuriToken')){
        this.getUserDetails()
    }
},
  methods: {
    async onUpdateProfile(){
      if(this.name == '' || this.email == '' || this.password == ''){
        alert("please fill all the details")
        return
      }
      let tok = this.$cookies.get('brahmapuriToken')
      let data = {
        name: this.name,
        email: this.email,
        password: this.password
      }
      try{
        let response = await this.$axios.$put('https://brahmapuri-server.herokuapp.com/api/auth/user',{data},{
        headers: {
          'x-access-token': tok
        }
      })
        if(response.success){
          this.$router.push("/")
        }
      } catch (err){
        console.log(err)
      }
    },
    async getUserDetails(){
       try{
         let v = this.$cookies.get('brahmapuriToken')
      let response = await this.$axios.$get("https://brahmapuri-server.herokuapp.com/api/auth/user", {
        headers: {
          'x-access-token': v
        }
      })
        this.name = response.user.name,
        this.email = response.user.email,
        this.password = response.user.password
    } catch (err) {
      console.log(err)
    }
    },
    onLogout(){
      this.$cookies.remove('brahmapuriToken')
      this.$router.push("/")
      // await this.$auth.logout()
    }
  }
}
</script>