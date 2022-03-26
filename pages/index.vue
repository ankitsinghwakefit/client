<template>
  <div>
    <!-- navbar -->
    <Navbarnew />
    <!-- main content -->

    <b-container fluid class="bv-example-row">
      <div v-if="!products">Loading Products, Hold Tight...</div>
      <b-row style="padding: 20px">
        <b-col
          xl="4"
          lg="4"
          md="6"
          sm="12"
          v-for="product in products"
          :key="product._id"
           style="margin-top:20px"><div>
              <div class="a-spacing-micro">
                      <div class="bestSeller">
                        <a href="#">Best Quality</a>
                      </div>
                    </div>
            <b-card
              no-body
              style="max-width: 20rem"
              :img-src="product.photo"
              img-alt="Image"
              img-top
            >
            
              <template #header>
                <h4 class="mb-0">{{ product.title }}</h4>
              </template>

              <b-card-body>
                <b-card-sub-title class="mb-2"
                  >Usages of {{ product.title }}</b-card-sub-title
                >
                <b-card-text>
                  {{ product.description }}
                </b-card-text>
              </b-card-body>

              <b-list-group flush>
                <b-list-group-item
                  >Stock Quantity: {{ product.stockQuantity }} Nos.</b-list-group-item
                >
                <b-list-group-item
                  >Price: Rs. {{ product.price }}/-</b-list-group-item
                >
              </b-list-group>

              <b-card-body>
                <a href="#" class="mybutton mybutton1" @click="addProductToCart(product)">Buy</a>
                <a href="#" class="mybutton mybutton1" @click="addProductToCart(product)">Add to cart</a>
                <router-link class="mybutton mybutton1" :to="product._id">View Product</router-link>
              </b-card-body>
            </b-card>
          </div></b-col
        >
      </b-row>
    </b-container>

    <!-- footer -->
    <Footer />
  </div>
</template>

<script>
import { mapActions } from "vuex"
import { mapGetters } from 'vuex'
import featuredProduct from "~/components/FeaturedProduct";
export default {
  name: "IndexPage",
   head() {
    return {
      title: "Home"
    };
  },
  data() {
    return {
      token: "",
      userName: "",
      products: ""
    };
  },
  components: {
    featuredProduct,
  },
  created() {
    // console.log("local storage in index", localStorage.getItem("brahmapuriToken"))
    if (this.$cookies.get("brahmapuriToken")) {
      let user = this.$cookies.get("brahmapuriToken")
        ? this.$cookies.get("brahmapuriToken")
        : null;
      this.token = user;
      this.getUserDetails();
    } else {
      this.token = null;
      this.userName = null;
      // alert("please login or register to buy products")
      this.$router.push("/signup")
    }
  },
   computed: {
    ...mapGetters(["getUser"])
  },
  mounted(){
    this.$axios.$get("https://brahmapuri-server.herokuapp.com/api/products")
    .then(response => {this.products = response.products})
    .catch(err => {console.log(err)})
  },
  // updated(){
  //   window.location.reload(true)
  // },
  // async asyncData({ $axios }) {
  //   try {
  //     let response = await $axios.$get(
  //       "https://brahmapuri-server.herokuapp.com/api/products"
  //     );
  //     return {
  //       products: response.products,
  //     };
  //   } catch (err) {
  //     console.log(err);
  //   }
  // },
  methods: {
    async getUserDetails() {
      try {
        let v = this.$cookies.get("brahmapuriToken");
        // let v = LocalStorage.getItem('brahmapuriToken') || this.$cookies.get('brahmapuriToken')
        let response = await this.$axios.$get(
          "https://brahmapuri-server.herokuapp.com/api/auth/user",
          {
            headers: {
              "x-access-token": v,
            },
          }
        );
        this.$store.commit("addUser", response.user)
        this.userName = response.user.name;
      } catch (err) {
        console.log(err);
      }
    },
    ...mapActions(["addProductToCart"])
  }
};
</script>

<style scoped>
.s-result-item {
  box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.75) !important;
  -webkit-box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.75) !important;
  -moz-box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.75) !important;
}
a.nuxt-link-active {
  font-weight: bold;
  color: #eee !important;
}
a.nuxt-link-exact-active {
  color: #00c58e !important;
}
.mybutton {
   background-color: #4CAF50; /* Green */
  border-radius: 8px;
  color: white;
  padding: 2px 9px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 13px;
  transition-duration: 0.4s;
  cursor: pointer;
}
.mybutton1 {
background-color: white; 
  color: black; 
  border: 2px solid #4CAF50;
}
.mybutton1:hover {
  background-color: #4CAF50;
  color: white;
}
</style>
