<template>
<div>
  <Navbar />
  <!-- edit address -->
  <main v-if="editAddress">
    <!--REGISTER ADDRESS-->
    <div class="registerAddress mt-3">
      <div class="container-fluid c-section">
        <div class="row">
          <div class="col-sm-3"></div>
          <div class="col-sm-6">
            <div class="a-section a-spacing-medium">
              <div class="a-subheader a-breadcrumb a-spacing-small">
                <!-- <ul>
                  <li>
                    <a href="#">
                      <span>Your Account</span>
                    </a>
                  </li>
                  <li class="a-breadcrumb-divider">›</li>
                  <li>
                    <a href="#">
                      <span>Your Adresses</span>
                    </a>
                  </li>
                  <li class="a-breadcrumb-divider">›</li>
                  <li class="active">
                    <a href="#">
                      <span>New Address</span>
                    </a>
                  </li>
                </ul> -->
              </div>
            </div>
            <div class="a-section">
              <h2>Edit your address</h2>
              <div class="a-section a-spacing-none a-spacing-top-small">
                <b>
                  Or pick up your packages at your convenience from our self-service locations. To add an brahmapuri-life-essentials Pickup Point or Locker, click
                  <a
                    href="#"
                  >here</a>.
                </b>
              </div>
              <!-- Error Message -->
              <div class="a-section a-spacing-none a-spacing-top-small">
                <b>{{message}}</b>
              </div>
              <form>
                <div class="a-spacing-medium a-spacing-top-medium">
                  <!-- Country / Region -->
                  <div class="a-spacing-top-medium">
                    <label style="margin-bottom: 0px;">Country/Region</label>
                    <select class="a-select-option" v-model="country">
                      <option>India</option>
                    </select>
                  </div>
                  <!-- Full name -->
                  <div class="a-spacing-top-medium">
                    <label style="margin-bottom: 0px;">Full Name</label>
                    <input type="text" v-model="fullName" :placeholder="targetedAddress.fullName" class="a-input-text" style="width: 100%;" />
                  </div>
                  <!-- Street Address -->
                  <div class="a-spacing-top-medium">
                    <label style="margin-bottom: 0px;">Street Address</label>
                    <input
                      type="text"
                      class="a-input-text"
                      style="width: 100%;"
                      v-model="streetAddress1"
                      :placeholder="targetedAddress.streetAddress"
                    />
                    <!-- Street Address 2 -->
                    <input
                      type="text"
                      class="a-input-text a-spacing-top-small"
                      style="width: 100%;"
                      v-model="streetAddress2"
                      placeholder="Apartment, suite, unit, building, floor, etc."
                    />
                  </div>
                  <!-- City -->
                  <div class="a-spacing-top-medium">
                    <label style="margin-bottom: 0px;">City</label>
                    <input type="text" v-model="city" class="a-input-text" :placeholder="targetedAddress.city" style="width: 100%;" />
                  </div>
                  <!-- State -->
                  <div class="a-spacing-top-medium">
                    <label style="margin-bottom: 0px;">State / Province / Region</label>
                    <input type="text" v-model="state" class="a-input-text" :placeholder="targetedAddress.state" style="width: 100%;" />
                  </div>
                  <!-- Zip Code -->
                  <div class="a-spacing-top-medium">
                    <label style="margin-bottom: 0px;">Zip Code</label>
                    <input type="text" v-model="zipCode" class="a-input-text" :placeholder="targetedAddress.zipCode" style="width: 100%;" />
                  </div>
                  <!-- Phone Number -->
                  <div class="a-spacing-top-medium">
                    <label style="margin-bottom: 0px;">Phone Number</label>
                    <input type="text" v-model="phoneNumber" class="a-input-text" :placeholder="targetedAddress.phoneNumber" style="width: 100%;" />
                    <div class="a-section a-spacing-none a-spacing-top-micro">
                      <span class="a-size-mini">May be used to assist delivery</span>
                    </div>
                  </div>
                  <div class="a-spacing-base a-spacing-top-medium">
                    <h3>Add delivery instructions</h3>
                  </div>
                  <!-- Delivery Instruction -->
                  <div class="a-spacing-top-medium">
                    <label
                      style="margin-bottom: 0px;"
                    >Do we need additional instructions to find this address?</label>
                    <textarea
                    v-model="deliveryInstructions"
                    :placeholder="targetedAddress.deliveryInstructions"
                      style="height:6em; width: 100%;"
                    ></textarea>
                  </div>
                  <!-- Security code -->
                  <div class="a-spacing-top-medium">
                    <label
                      style="margin-bottom: 0px;"
                    >Do we need a security code or a call box number to access this building?</label>
                    <input type="text" v-model="securityCode" class="a-input-text" style="width: 100%;"  :placeholder="targetedAddress.securityCode" />
                  </div>
                  <div class="a-spacing-top-medium">
                    <label style="margin-bottom: 0px;">Weekend delivery</label>
                    <a href="#">
                      <i class="fas fa-angle-down"></i> Which days can you receive packages?
                    </a>
                  </div>
                  <div class="a-spacing-top-medium"></div>
                  <hr />
                  <div class="a-spacing-top-medium">
                    <span>
                      <b>Make sure your address is correct</b>
                    </span>
                  </div>
                  <div>
                    <span>If the address contains typos or other errors, your package may be undeliverable.</span>
                  </div>
                  <div class="a-spacing-top-small">
                    <span>
                      <a href="#">Tips for entering addresses</a>
                    </span>
                    <span>|</span>
                    <span>
                      <a href="#">APO/FPO address tips</a>
                    </span>
                  </div>
                  <div class="a-spacing-top-large">
                    <span class="a-button-register">
                      <span class="a-button-inner">
                        <span class="a-button-text" @click="onAddAddress">Update Address</span>
                      </span>
                    </span>
                  </div>
                </div>
              </form>
            </div>
          </div>
          <div class="col-sm-3"></div>
        </div>
      </div>
    </div>
    <!-- edit address -->
    <!--/REGISTER ADDRESS-->
  </main>
  <!--MAIN-->
  <main>
    <!--REGISTER ADDRESS-->
    <div class="registerAddress mt-3">
      <div class="container-fluid c-section">
        <div class="row">
          <div class="col-sm-2"></div>
          <div class="col-sm-10">
            <div class="a-section a-spacing-medium">
              <div class="a-subheader a-breadcrumb a-spacing-small">
                <ul>
                  <li>
                    <a href="#">
                      <span>Your Account</span>
                    </a>
                  </li>
                  <li class="a-breadcrumb-divider">›</li>
                  <li class="active">
                    <a href="#">
                      <span>Your Adresses</span>
                    </a>
                  </li>
                </ul>
              </div>
              <h1 class="a-spacing-medium a-spacing-top-medium">Your Addresses</h1>
              <!-- Message from Server -->
              <div class="a-section a-spacing-none a-spacing-top-small">
                <b>{{message}}</b>
              </div>
              <div class="a-spacing-double-large">
                <div class="row a-spacing-micro">
                  <div v-if="showAddAddress == 0" class="col-lg-4 col-md-5 col-sm-12 pb-2">
                    <nuxt-link
                      to="/address"
                      class="a-link-normal add-new-address-button"
                      style="text-decoration:none;"
                    >
                      <div class="a-box first-desktop-address-tile">
                        <div class="a-box-inner a-padding-extra-large">
                          <i class="far fa-plus"></i>
                          <h2 class="a-color-tertiary">Add Address</h2>
                        </div>
                      </div>
                    </nuxt-link>
                  </div>
                  <!-- Address -->
                  <div class="col-lg-4 col-md-4 col-sm-12 pl-md-0 pb-2" v-for="(addres,index) in address" :key="addres._id">
                    <div class="a-box a-spacing-none normal-desktop-address-tile">
                      <div class="a-box-inner a-padding-none">
                        <div class="address-section-no-default">
                          <div class="a-spacing-small">
                            <ul class="a-unordered-list a-nostyle a-vertical">
                              <li>
                                <h5>
                                  <!-- Address Fullname -->
                                  <b>{{addres.fullName}}</b>
                                </h5>
                              </li>
                              <!-- Address street address -->
                              <li>{{addres.streetAddress}}</li>
                              <!-- Address city state zip code -->
                              <li>{{addres.city}}, {{addres.state}}, {{addres.zipCode}}</li>
                              <!-- Address country -->
                              <li>{{addres.country}}</li>
                              <!-- Address Phone number -->
                              <li>Phone number: {{addres.phoneNumber}}</li>
                            </ul>
                          </div>
                        </div>
                      </div>
                      <!-- Delete Button -->
                      <div class="edit-address-desktop-link">
                        <a href="#" @click="onEditAddress(addres)">Edit</a>
                        &nbsp; | &nbsp;
                        <a href="#" @click="onDeleteAddress(addres._id,index)">Delete</a>
                        <!-- &nbsp; | &nbsp; -->
                        <!-- Set Address as Default -->
                        <!-- <a href="#" @click="onSetDefault(addres._id)">Set as Default</a> -->
                      </div>
                    </div>
                  </div>
                  <div class="col-lg-4 col-md-3 col-sm-12"></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!--/REGISTER ADDRESS-->
  </main>
  <!--/MAIN-->
  <!-- edit address -->
  
  <!-- / edit address -->
  <Footer />
  </div>
</template>

<script>
export default {
   head() {
    return {
      title: "Your Address"
    };
  },
   data() {
    return {
      showAddAddress: true,
      address: null,
      targetedAddress: "",
      message:'',
      editAddress: false,
      country: "",
      fullName: "",
      streetAddress1: "",
      streetAddress2: "",
      city: "",
      state: "",
      zipCode: "",
      phoneNumber: "",
      deliveryInstructions: "",
      securityCode: "",
      targetedAddressId: ""
    };
  },
  mounted(){
    console.log("local", localStorage.getItem('brahmapuriToken'), "cook",this.$cookies.get('brahmapuriToken'))
    let v = localStorage.getItem('brahmapuriToken') || this.$cookies.get('brahmapuriToken')
    if(!v){
      alert("Please login or register to add address")
      this.$router.push('/login')}
    this.$axios.$get("https://brahmapuri-server.herokuapp.com/api/address",
    {
            headers: {
              "x-access-token": v,
            },
          })
    .then(response => {
      this.showAddAddress = response.address.length
      console.log("null address",typeof(this.showAddAddress))
      this.address = response.address}
      )
    .catch(err => {console.log(err)})
  },
  methods:{
    async onDeleteAddress(id,index){
    try{
      let v = this.$cookies.get('brahmapuriToken') || localStorage.getItem('brahmapuriToken')
        let response = await this.$axios.$delete(`https://brahmapuri-server.herokuapp.com/api/address/${id}`,{
            headers: {
              "x-access-token": v,
            },
          })
          console.log("response", response)
        if(response.success){
          this.message = response.message
          this.address.splice(index,1)
           this.$router.push("/")
          // window.location.reload(true)
        }
      }catch(err){
        this.message = err.message
        console.log(err)
      }
    },
    // async onSetDefault(id){
    //   try{
    //     let response = await this.$axios.$put(`http://localhost:8000/api/address/set/default`, {id:id},{
    //         headers: {
    //           "x-access-token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2MWNkM2RjOTVlNjQzM2QxM2MyNGI4MjYiLCJuYW1lIjoiYW5raXQgc2luZ2giLCJlbWFpbCI6ImFua2l0c2luZ2h3YWtlZml0QGdtYWlsLmNvbSIsInBhc3N3b3JkIjoiJDJiJDEwJEo0OWdTbTNJRE9KRmM3T2ttSXNBME9lcG4zWEViTWRuekJDTnpOelhrNExUWHBiLjJhVEhtIiwiX192IjowLCJpYXQiOjE2NDEyMTU3NjgsImV4cCI6MTY0MTgyMDU2OH0.6m6ml5eVVY2uLNB2b5Z1zBR2BMsE9EwTUzUXJV5W4X0",
    //         },
    //       })
    //     if(response.success){
    //       this.message = response.message
    //       await this.$auth.fetchUser()
    //     }
    //   } catch(err){
    //     this.message = err.message
    //     console.log(err)
    //   }
    // },
    async onEditAddress(address){
      console.log("this fullname", this.fullName)
      this.editAddress = true
      this.targetedAddress = address
      this.targetedAddressId = address._id
    },
    async onAddAddress(){
      try{
        let data = {
      country: this.country,
      fullName: this.fullName,
      streetAddress: this.streetAddress,
      city: this.city,
      state: this.state,
      zipCode: this.zipCode,
      phoneNumber: this.phoneNumber,
      deliveryInstructions: this.deliveryInstructions,
      securityCode: this.securityCode
      }
      let v = this.$cookies.get('brahmapuriToken') || localStorage.getItem('brahmapuriToken')
      let response = await this.$axios.$put(`https://brahmapuri-server.herokuapp.com/api/address/${this.targetedAddressId}`, data,  {
            headers: {
              "x-access-token": v,
            },
          })
      if(response.success){
        this.editAddress = false
         this.$router.push("/")
        // window.location.reload(true)
      }
      } catch(err){

      }
    }
  }
}
</script>

