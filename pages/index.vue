<template>
  <div>
    <!-- navbar -->
    <Navbar :userName="userName" :token="token" />
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
                <a href="#" class="card-link">Buy</a>
                <a href="#" class="card-link">Add to cart</a>
                <router-link class="card-link" :to="product._id">View Product</router-link>
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
import featuredProduct from "~/components/FeaturedProduct";
export default {
  name: "IndexPage",
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
    if (this.$cookies.get("brahmapuriToken")) {
      this.$forceUpdate();
      let user = this.$cookies.get("brahmapuriToken")
        ? this.$cookies.get("brahmapuriToken")
        : null;
      this.token = user;
      this.getUserDetails();
    } else {
      this.token = null;
      this.userName = null;
    }
  },
  mounted(){
    this.$axios.$get("https://brahmapuri-server.herokuapp.com/api/products")
    .then(response => {this.products = response.products})
    .catch(err => {console.log(err)})
  },
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
        let response = await this.$axios.$get(
          "https://brahmapuri-server.herokuapp.com/api/auth/user",
          {
            headers: {
              "x-access-token": v,
            },
          }
        );
        this.userName = response.user.name;
      } catch (err) {
        console.log(err);
      }
    },
  },
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
</style>
