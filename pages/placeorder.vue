<template>
  <div>
    <Navbar />
    <body>
      <!--SHIPPING ADDRESS-->
      <div class="container-fluid">
        <div class="shipping-address">
          <!-- <div class="navbarShipping a-spacing-large">
        <nuxt-link to="/">
        <img src="img/blogo.jpg" alt="logo" style="width:50px; height:50px" class="img-fluid" />
        </nuxt-link>
      </div> -->
          <div class="a-row">
            <div class="a-size-large a-text-bold a-spacing-mini">
              Review your order
            </div>
            <div class="a-row a-spacing-small a-size-mini"></div>
          </div>
          <div class="row">
            <div class="col-xl-9 col-lg-8 col-md-9 col-sm-12">
              <div class="a-row a-spacing-large"></div>
              <div class="spc-top a-box a-spacing-small">
                <div class="a-box-inner">
                  <div class="row">
                    <div class="col-xl-4 col-lg-6 col-sm-6 col-6">
                      <div class="a-spacing-base">
                        <div class="a-row">
                          <strong>
                            Shipping address
                            <small>
                              <router-link to="/alladdress">Change</router-link>
                            </small>
                          </strong>
                        </div>
                        <div class="a-row">
                          <div class="displayAddressDiv">
                            <!-- User's address -->
                            <ul class="displayAddressUL">
                              <li>{{ address.fullName }}</li>
                              <li>{{ address.streetAddress }}</li>
                              <li>{{ address.city }}</li>
                              <li>
                                {{ address.state }} - {{ address.zipCode }}
                              </li>
                              <li>{{ address.country }}</li>
                              <li>
                                Phone:
                                <span dir="ltr">{{ address.phoneNumber }}</span>
                              </li>
                            </ul>
                          </div>
                        </div>
                      </div>
                    </div>
                    <div class="col-xl-4 col-lg-6 col-sm-6 col-6">
                      <div class="a-spacing-base">
                        <div class="a-row">
                          <strong>
                            Payment Method
                            <!-- <small>
                              <a href="#">Change</a>
                            </small> -->
                          </strong>
                        </div>
                        <div class="a-row">
                          <ul class="no-bullet-list">
                            <li class="a-spacing-micro">
                              <span class="a-list-item">
                                <span>
                                  <img src="img/visa.gif" class="img-fluid" />
                                </span>
                                ending in
                                <span>6397</span>
                              </span>
                            </li>
                          </ul>
                        </div>
                      </div>
                      <div class="a-row a-spacing-base">
                        <div class="a-row">
                          <strong>
                            Billing Address
                            <!-- <small>
                              <a href="#">Change</a>
                            </small> -->
                          </strong>
                        </div>
                        <span>Same as shipping address</span>
                      </div>
                    </div>
                    <div class="col-xl-4 col-lg-6 col-sm-12 col-12">
                      <div class="a-spacing-base">
                        <div class="a-spacing-mini">
                          <span>
                            <strong>Gift cards &amp; promotional codes</strong>
                          </span>
                        </div>
                        <div class="row">
                          <div
                            class="col-xl-8 col-lg-7 col-md-7 col-sm-7 col-8 pr-0"
                          >
                            <input
                              type="text"
                              autocomplete="off"
                              class="a-input-text"
                              placeholder="Enter Code"
                            />
                          </div>
                          <div
                            class="col-xl-4 col-lg-5 col-md-5 col-sm-5 col-4"
                          >
                            <span class="a-buton-apply-code">
                              <span class="a-button-inner">
                                <span class="a-button-text">Apply</span>
                              </span>
                            </span>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div class="spc-orders a-box a-spacing-small">
                <div class="a-box-inner">
                  <div class="shipping-group">
                    <!-- Estimated delivery -->
                    <div
                      class="a-row a-color-state a-text-bold a-size-medium a-spacing-small"
                    >
                      Estimated delivery: Within 10 days after placing order.
                    </div>
                    <div class="row">
                      <!-- Cart -->
                      <div class="col-xl-6 col-lg-7 col-sm-6 col-12">
                        <div
                          class="a-row a-spacing-base"
                          v-for="product in getCart"
                          :key="product._id"
                        >
                          <div class="row">
                            <!-- Product's photo -->
                            <div class="col-sm-3 col-3">
                              <img :src="product.photo" style="width: 100%" />
                            </div>
                            <!-- Product's Title -->
                            <div class="col-sm-9 col-9">
                              <div class="a-row">
                                <strong>{{ product.title }}</strong>
                              </div>
                              <!-- Product's owner name -->
                              <div class="a-row a-size-small">
                                by product owner name
                              </div>
                              <div class="a-row">
                                <!-- Product's price -->
                                <span class="a-color-price a-spacing-micro">
                                  <strong dir="ltr"
                                    >Rs.
                                    {{
                                      product.price * product.quantity
                                    }}</strong
                                  >
                                </span>
                              </div>
                              <div class="a-row">
                                <span class="availability a-color-success"
                                  >In Stock.</span
                                >
                              </div>
                              <div class="a-row">
                                <!-- Product's quantity -->
                                <strong
                                  >Quantity: {{ product.quantity }}</strong
                                >
                              </div>
                              <div class="a-row a-color-secondary a-size-small">
                                Sold by:&nbsp;brahmapuri-life-essentials
                              </div>
                              <div class="a-row">
                                <div class="a-row a-spacing-top-micro">
                                  <span class="a-button-small">
                                    <span class="a-button-inner">
                                      <i
                                        class="a-icon checkout-giftbox-icon"
                                      ></i>
                                      <a
                                        href="#"
                                        class="a-button-text gift-popover-link"
                                        >Add a gift receipt</a
                                      >
                                    </span>
                                  </span>
                                </div>
                                <div class="a-row">
                                  <span class="a-color-secondary a-size-mini"
                                    >and see other gift options</span
                                  >
                                </div>
                              </div>
                            </div>
                          </div>
                        </div>
                      </div>
                      <div class="col-xl-6 col-lg-5 col-sm-6 col-12">
                        <div class="a-row shipping-speeds">
                          <!-- <fieldset>
                        <span class="shipping-speeds-title a-size-medium">
                          <b>Choose a delivery option:</b>
                        </span>
                        <div class="a-spacing-mini wednesday">
                          <input type="radio" name="order0" />
                          <span class="a-radio-label">
                            <span class="a-color-success">
                              <strong>Averages 7 business days</strong>
                            </span>
                            <br />
                            <span
                              class="a-color-secondary"
                            >$13.98&nbsp;-&nbsp;Standard International Shipping - No Tracking</span>
                          </span>
                        </div>
                        <br />
                        <div class="a-spacing-mini tuesday">
                          <input type="radio" name="order0" />
                          <span class="a-radio-label">
                            <span class="a-color-success">
                              <strong>Averages 3 business days</strong>
                            </span>
                            <br />
                            <span class="a-color-secondary">$49.98&nbsp;-&nbsp;Shipping</span>
                          </span>
                        </div>
                      </fieldset> -->
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <div class="col-xl-3 col-lg-4 col-md-3 col-sm-12 pl-0">
              <div class="a-box-group">
                <div class="a-box a-first">
                  <div class="a-box-inner">
                    <div class="a-row a-spacing-micro">
                      <!-- <a href="https://rzp.io/l/pay-brahmapuri-life-essentials">
                        <span class="a-button-place-order"
                          >Place your order in INR</span
                        >
                      </a> -->
                      <button class="a-button-place-order" id="rzp-button1" @click="callPayU">Place your order in INR</button>
                    </div>
                    <div
                      class="a-row a-spacing-small a-size-small a-text-center"
                    >
                      By placing your order, you agree to
                      brahmapuri-life-essentials
                      <router-link to="/termsandconditions">conditions of use</router-link> and 
                       <router-link to="/privacypolicy">Privacy Notice</router-link>.
                    </div>
                    <div class="a-row">
                      <!-- <div id="tfx-header">
                    <div class="a-box a-alert-info a-spacing-small">
                      <div class="a-box-inner alert-info-no-icon">
                        <strong>
                          Amazon Currency Converter is Enabled. &nbsp;
                          <a
                            href="#"
                            class="a-size-mini"
                          >Learn More</a>
                        </strong>
                      </div>
                    </div>
                  </div> -->
                      <h3 class="a-spacing-micro a-size-base">Order Summary</h3>
                      <div class="order-summary" style="font-size: 12px">
                        <div class="row">
                          <!-- Cart's total price -->
                          <div class="col-sm-6">Items:</div>
                          <div class="col-sm-6 text-right">
                            INR Rs. {{ getCartTotalPrice }}
                          </div>
                        </div>
                        <div class="row">
                          <!-- Shipping cost -->
                          <div class="col-sm-6">Shipping & handling:</div>
                          <div class="col-sm-6 text-right">INR 00</div>
                        </div>
                        <div class="row mt-2">
                          <div class="col-sm-6"></div>
                          <div class="col-sm-6 text-right">
                            <hr />
                          </div>
                        </div>
                        <!-- Total Price with Shipping -->
                        <div class="row">
                          <div class="col-sm-6">Total Tax:</div>
                          <div class="col-sm-6 text-right">
                            INR {{ totalTax }}
                          </div>
                        </div>
                        <div class="row">
                          <div class="col-sm-6">
                            Estimated tax to be collected:
                          </div>
                          <div class="col-sm-6 text-right">INR 3% of total</div>
                        </div>
                        <hr />
                        <div class="row">
                          <div class="col-sm-6">
                            <div
                              class="a-color-price a-size-medium a-text-bold"
                            >
                              Order total:
                            </div>
                          </div>
                          <div class="col-sm-6 text-right">
                            <!-- Total Price with Shipping -->
                            <div
                              class="a-color-price a-size-medium a-text-bold"
                            >
                              INR {{ orderPriceTotal }}
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div class="a-box a-last a-color-alternate-background">
                  <div class="a-box-inner">
                    <div class="a-spacing-base">
                      <div class="a-row">
                        <span>
                          <i class="fas fa-caret-down"></i>
                          <a href="#">Selected payment currency</a>
                        </span>
                        <fieldset class="pl-3">
                          <span style="margin-left: 1rem">
                            <input
                              type="radio"
                              class="no-js-hide"
                              value="transactional"
                            />
                            <span class="a-radio-label">INR</span>
                          </span>
                          <div class="a-row">
                            <span class="a-size-mini">
                              <a href="#">(Change card currency)</a>
                            </span>
                          </div>
                        </fieldset>
                      </div>
                    </div>
                    <div class="a-size-mini">
                      <div class="a-row a-spacing-mini mb-1">
                        Please note that your country may charge import duties,
                        taxes and fees that you may have to pay ahead of
                        delivery.
                        <a href="#">Learn more</a>
                      </div>
                      <div class="a-row a-spacing-mini mb-1">
                        <a href="#">How are shipping costs calculated?</a>
                      </div>
                      <div class="a-row a-spacing-mini">
                        <a href="#">Why didn't I qualify for free shipping?</a>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="a-row a-spacing-small a-spacing-top-small">
            <p class="a-color-secondary a-size-mini">
              Do you need help? Explore our
              <a href="#">Help pages</a> or
              <a href="#">contact us</a>
            </p>
            <p class="a-color-secondary a-size-mini">
              For an item sold by brahmapuri-life-essentials: When you click the
              "Place your order" button, we'll send you an email message
              acknowledging receipt of your order. Your contract to purchase an
              item will not be complete until we send you an email notifying you
              that the item has been shipped.
            </p>
            <p id="state-sales-tax-info" class="a-color-secondary a-size-mini">
              Colorado, Oklahoma, South Dakota and Vermont Purchasers:
              <a href="#"
                >Important information regarding sales tax you may owe in your
                State</a
              >
            </p>
            <div class="a-color-secondary a-size-mini">
              
            </div>
          </div>
          <hr />
          <p class="a-size-small a-text-center a-color-secondary" data-testid>
             <router-link to="/termsandconditions">conditions of use</router-link> | 
                       <router-link to="/privacypolicy">Privacy Notice</router-link> ©
            2003-2022, brahmapuri-life-essentials, Inc.
          </p>
        </div>
      </div>
      <!--/SHIPPING ADDRESS-->
    </body>
    <Footer />
  </div>
</template>

<script>
// import { URLSearchParams } from "url"
import { mapGetters } from "vuex";
export default {
   head() {
    return {
      title: "Place Your Order"
    };
  },
  data() {
    return {
      address: "",
      payOrderId: "",
      payResponse: "",
      orderAddress: "",
      orderEmail: "",
      orderName: "",
      orderProducts: "",
      orderCart: ""
    };
  },
  computed: {
    ...mapGetters(["getCart", "getCartTotalPrice", "getUser", "getCartTotal"]),
    totalTax(){
      return Math.ceil(this.getCartTotalPrice * .03)
    },
    orderPriceTotal(){
      return this.getCartTotalPrice + Math.ceil(this.getCartTotalPrice * .03)
    }
    //  isDisabled() {
    //    if(this.orderPriceTotal == 0){
    //      return true
    //    } else {
    //      return true
    //    }
    //   },
  },
  async mounted() {
    console.log("total price", this.orderPriceTotal)
    let v = localStorage.getItem('brahmapuriToken') || this.$cookies.get('brahmapuriToken')
    // if (!process.client) return;
    // const savedData = localStorage.getItem("vuex");
    // let a = JSON.parse(savedData);
    // let finalPrice = a.cartToatl;

    if (!v) {
      alert("Please login or register to add items and checkout");
      this.$router.push("/login");
    }
    const [firstResponse, secondResponse] = await Promise.all([
      this.$axios.$get(`https://brahmapuri-server.herokuapp.com/api/address`, {
        headers: {
          "x-access-token": v,
        },
      }),
      this.$axios.$post(`https://brahmapuri-server.herokuapp.com/api/payment`, {
        amount: this.orderPriceTotal,
      }),
    ]);
    console.log("getting address", firstResponse);
    if (firstResponse.success && firstResponse.address.length > 0) {
      this.address = firstResponse.address[0];
    } else {
      // alert("Please add your Delivery Address");
      this.$router.push("/");
    }
    this.payOrderId = secondResponse.id;
    this.orderName = this.getUser.name
    this.orderEmail = this.getUser.email
    let oPrdoucts = []
    let oObj = {}
    this.getCart.map(prod =>{
      oObj.title = prod.title
      oObj.qty = prod.quantity
      oObj.price = prod.price
      oPrdoucts.push(oObj)
      oObj = {}
    })
    let oAddress = []
    let oAddressObj = {}
    oAddressObj.address = this.address.streetAddress
    oAddressObj.phoneNumber = this.address.phoneNumber
    oAddressObj.city = this.address.city
    oAddressObj.state = this.address.state
    oAddressObj.zipCode = this.address.zipCode
    oAddress.push(oAddressObj)
    this.orderProducts = oPrdoucts
    this.orderAddress = oAddress
    this.orderCart = this.getCart
    console.log("orderCart", this.getCart, "orderAddress", this.orderAddress, "orderProducts", this.orderProducts)
  },
  methods: {
    callPayU() {
      console.log("cart total", this.getCartTotal);
      // this.$axios.$get('http://localhost:8000/api/payment').then(res =>{
      //   console.log("response", res)
      var options = {
        // "my key": "my secret key",
        key: this.$config.myPublicVariable,
        amount: this.getCartTotal, // 2000 paise = INR 20
        currency: "INR",
        name: "Brahmapuri-Life-Essentials",
        description: "Vibrated, Organic, Hand Made.",
        image: "img/blogo.jpg",
        order_id: this.payOrderId,
        handler: (response) => {
          let passData = {
            razorpay_payment_id: response.razorpay_payment_id,
            razorpay_order_id: response.razorpay_order_id,
            razorpay_signature: response.razorpay_signature,
            razorpay_order_id_my: this.payOrderId
          };
          this.payResponse = passData
          console.log("payResponse", this.payResponse)
          this.mycal(this.payResponse);
          alert(response.razorpay_payment_id);
          alert(response.razorpay_order_id);
          alert(response.razorpay_signature);
        },
        prefill: {
          name: this.getUser.name,
          email: this.getUser.email,
          contact: this.address.phoneNumber,
        },
        notes: {
          address: "Hello World",
        },
        theme: {
          color: "#142863",
        },
      };
      var rzp1 = new Razorpay(options);
      rzp1.on("payment.failed", (response) => {
        let failData = {
          code: response.error.code,
          description: response.error.description,
          source: response.error.source,
          step: response.error.step,
          reason: response.error.reason,
          order_id: response.error.order_id,
          payment_id: response.error.payment_id,
        };
        this.payResponse = failData
        console.log("payResponse", this.payResponse)

        this.mycallFail(this.payResponse);
        alert(response.error.code);
        alert(response.error.description);
        alert(response.error.source);
        alert(response.error.step);
        alert(response.error.reason);
        alert(response.error.metadata.order_id);
        alert(response.error.metadata.payment_id);
      });

      document.getElementById("rzp-button1").onclick = function (e) {
        rzp1.open();
        e.preventDefault();
      };
    },
    async mycal(passPaymentData) {
      let v = localStorage.getItem('brahmapuriToken') || this.$cookies.get('brahmapuriToken')
      let orderDataOnSuccess = {
        name: this.orderName,
        email: this.orderEmail,
        address: this.orderAddress,
        productOrder: this.orderProducts
      }
     let passResponse = {
        passPaymentData,
        orderDataOnSuccess,
        cart: this.orderCart
      }
      console.log("v",v)
      console.log("mycal called with passPaymentData", passPaymentData);
      console.log("mycal called with orderDataOnSuccess", orderDataOnSuccess);
      console.log("mycal called with", passResponse);
      // let abc = JSON.stringify({passResponse})
      await this.$axios
        .$post("https://brahmapuri-server.herokuapp.com/api/payment/pass", {
          passResponse,
        },{
        headers: {
          "x-access-token": v,
        },
      })
        .then((res) => {
         if(res.success){
           this.$store.commit("clearCart");
           this.$router.push("/")
         }
        })
        .catch((err) => {
          console.log(err);
        });
    },
    async mycallFail(failResponse) {
      console.log("mycallFail called with", failResponse);
      await this.$axios
        .$post("https://brahmapuri-server.herokuapp.com/api/payment/fail", {
          failResponse,
        })
        .then((res) => {
                console.log("mycallFail axios response with", res);
          alert("Your Payment failed, Please try again...");
        });
    },
  },
};
</script>
