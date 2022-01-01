<template>
    <header class="nav-opt-sprite nav-location-us nav-lang-en nav-ssl nav-unrec">
      <div class="container-fluid desktop-nav">
        <div class="row">
          <!-- logo -->
          <div class="col-sm-2">
            <div class="logo-area">
              <router-link to="/">
                <img src="http://brahmapuri.org.in/images/logo11%20copy.png" alt="logo" class="img-fluid" />
              </router-link>
            </div>
          </div>
          <!-- search box -->
          <div class="col-sm-6 pt-0">
            <Search />
          </div>
          <div class="col-sm-4"></div>
        </div>

        <div class="row">
          <!-- Delivery -->
          <div class="col-xl-2 col-lg-2 col-md-2 col-sm-2 pl-2">
            <div class="nav-global-location">
              <nuxt-link to="#" class="nav-a nav-a-2">
                <div class="nav-sprite" id="nav-packard-glow-loc-icon"></div>
                <div id="glow-ingress-block">
                  <span class="nav-line-1" id="glow-ingress-line1">Deliver to</span>
                  <span class="nav-line-2" id="glow-ingress-line2">Chhindwada</span>
                </div>
              </nuxt-link>
            </div>
          </div>
          <!-- Shopping -->
          <div class="col-xl-6 col-lg-5 col-md-4 col-sm-6 p-0">
            <div class="nav-fill">
              <!-- <div class="nav-shop">
                <nuxt-link to="/history" class="nav-a nav-a-2 nav-single-row-link">
                <span class="nav-line-2">
                  Browsing History
                  <span class="nav-icon nav-arrow" style="visibility: visible"></span>
                </span>
                </nuxt-link>
              </div> -->

              <div class="nav-xshop-container">
                <div class="nav-xshop">
                  <router-link to="/" class="nav-a">Home</router-link>
                  <a href="#" class="nav-a">Contact Us</a>
                  <router-link to="/signup" class="nav-a">Register</router-link>
                  <a href="#" class="nav-a">About Us</a>
                  <router-link to="/login" class="nav-a">Login</router-link>
                </div>
              </div>
            </div>
          </div>
            <!-- accounts and order -->
          <div class="col-xl-4 col-lg-5 col-md-6 col-sm-4 p-0">
            <div class="nav-tools">
              <a href="#" id="icp-nav-flyout" class="nav-a nav-a-2 icp-link-style-2">
                <span class="icp-nav-link-inner">
                  <span class="nav-line-1">
                    <span class="icp-nav-globe-img-2"></span>
                    <span class="icp-nav-language">EN</span>
                  </span>

                  <span class="nav-line-2">
                    &nbsp;
                    <span class="nav-icon nav-arrow" style="visibility: visible">

                    </span>
                  </span>
                </span>
              </a>
              <span class="icp-nav-link-border"></span>
              <template v-if="token">
                <nuxt-link to="/profile" class="nav-a nav-a-2" id="nav-link-accountlist" tabindex="0">
                <span class="nav-line-1">Hello,</span>
                <span class="nav-line-2">{{userName}}</span>
              </nuxt-link>
              </template>
              <template v-else>
              <nuxt-link to="/login" class="nav-a nav-a-2" id="nav-link-accountlist" tabindex="0">
                <span class="nav-line-1">Hello, Sign in</span>
                <span class="nav-line-2">
                  Account &amp; Lists
                  <span class="nav-icon nav-arrow" style="visibility: visible"></span>
                </span>
              </nuxt-link>
              </template>
              <nuxt-link to="/orders" class="nav-a nav-a-2 nav-single-row-link">
              <span class="nav-line-1"></span>
              <span class="nav-line-2">Orders</span>
              </nuxt-link>

              <nuxt-link to="/cart" class="nav-a nav-a-2" id="nav-cart">
              <span aria-hidden="true" class="nav-line-1"></span>
               <span aria-hidden="true" class="nav-line-2">Cart</span>
              <span class="nav-cart-icon nav-sprite"></span>
              <span id="nav-cart-count" aria-hidden="true" class="nav-cart-count nav-cart-0">0</span>
              </nuxt-link>
            </div>
          </div>
        </div>
      </div>
    </header>
</template>

<script>
import Search from '~/components/Search'
export default {
  components: {
    Search
  },
  data(){
    return{
      
    }
  },
  props: {
    token: '',
      userName: ''
  }
//   created () {
//           let user = this.$cookies.get('auth._token.local')? this.$cookies.get('auth._token.local') : null;
//         this.token = user
//         this.getUserDetails()
// },
  // computed: {
  //   userLoginStatus(){
  //     console.log("computed called")
  //     this.myTest()
  //     // let userToken = Window.localStorage.getItem("auth._token.local") || null
  //     // console.log("user in local", userToken)
  //     return userToken
  //   }
  // },
  // methods: {
  //   async getUserDetails(){
  //      try{
  //        console.log("called userDeatails")
  //     let response = await $axios.$post("http://localhost:8000/api/auth/user", {
  //       headers: {
  //         'x-access-token': this.token
  //       }
  //     })
  //     console.log("user details",response)
  //       // this.userName = response.products
  //   } catch (err) {
  //     console.log(err)
  //   }
  //   }
  // }
}
</script>