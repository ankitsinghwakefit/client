<template>
    <div>
  <b-navbar toggleable="lg" type="dark" variant="dark">
    <div class="my-logo"><router-link to="/">
                <img src="img/blogo.jpg" alt="logo" class="img-fluid" />
              </router-link>
    </div>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item to="/">Products</b-nav-item>
        <b-nav-item to="/contact">Contact Us</b-nav-item>
        <b-nav-item to="/about">About Us</b-nav-item>
        <b-nav-item  to="/signupnew" v-show="!getUser" class="nav-a">Register</b-nav-item >
        <b-nav-item v-if="getUser" @click="logoutUser" to="#">Logout</b-nav-item>
        <b-nav-item v-else @click="loginUser">Login</b-nav-item>
        <b-nav-item to="/alladdress">Your Address</b-nav-item>

      </b-navbar-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
        <!-- <b-nav-form>
          <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
          <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
        </b-nav-form> -->

        <b-nav-item-dropdown text="Lang" right>
          <b-dropdown-item href="#">EN</b-dropdown-item>
          <b-dropdown-item href="#">Hindi</b-dropdown-item>
        </b-nav-item-dropdown>
        <b-nav-item right to="/orders" class="nav-a nav-a-2 nav-single-row-link">
        Orders
              <!-- <span class="nav-line-1"></span> -->
              <!-- <span class="nav-line-2">Orders</span> -->
              </b-nav-item>

              <b-nav-item right to="/cart" class="nav-a nav-a-2" id="nav-cart">
              <!-- <span aria-hidden="true" class="nav-line-1"></span>
               <span aria-hidden="true" class="nav-line-2">Cart</span> -->
              <!-- <span class="nav-cart-icon nav-sprite"></span> -->
              
              <b-icon icon="cart-check-fill" style="color: #F5F5F5;width: 40px; height: 30px;"></b-icon>
              <span id="nav-cart-count" aria-hidden="true" class="nav-cart-count nav-cart-0">{{getCartLength}}</span>
              </b-nav-item>

        <b-nav-item-dropdown right>
          <!-- Using 'button-content' slot -->
          <template #button-content>
            <em v-if="getUser">Hello, {{getUser.name}}</em>
            <em v-else>Login</em>
          </template>
          <b-dropdown-item v-if="getUser" to="/profile">Profile</b-dropdown-item>
          <b-dropdown-item @click="logoutUser">Sign Out</b-dropdown-item>
        </b-nav-item-dropdown>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  data(){
    return{
      
    }
  },
  computed: {
    ...mapGetters(["getCartLength", "getUser"])
  },
  methods: {
     logoutUser(){
       localStorage.removeItem("brahmapuriToken");
       this.$cookies.remove("brahmapuriToken")
       this.$store.commit("logoutUser")
      //  window.location.reload(true)
       this.$router.push("/loginnew")
     },
     loginUser(){
        this.$router.push("/loginnew")
     }
    }
}
</script>

<style scoped>
.my-logo {
    width: 50px !important;
    height: 50px !important;
}
.navbar.navbar-dark.bg-dark{
    background-color: #0B5A4F!important;
    min-height: 100px;
}
.navbar-dark .navbar-nav .nav-link{
    color:rgb(218, 214, 214)!important;
    font-size: 20px;
}
.nav-link .dropdown-toggle {
  color:rgb(218, 214, 214)!important;
    font-size: 20px;
}
@media screen and (max-width: 1024px) {
  .navbar-dark .navbar-nav .nav-link{
    color:rgb(218, 214, 214)!important;
    font-size: 18px;
}
}
</style>