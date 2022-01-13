<template>
<div>
  <Navbar />
  <!--MAIN-->
  <main>
    <!--YOUR ORDER-->
    <div class="container-fluid your-order">
      <div class="row">
        <div class="col-xl-2 col-lg-1 col-md-12"></div>
        <div class="col-xl-8 col-lg-9 col-md-12">
          <div class="a-spacing-large a-spacing-top-small a-subheader a-breadcrumb">
            <ul class="a-unordered-list a-nostyle a-horizontal">
              <li>
                <span class="a-list-item">
                  <a class="a-link-normal">
                    <span>Your Account</span>
                  </a>
                </span>
              </li>
              <li class="a-breadcrumb-divider">›</li>
              <li>
                <span class="a-list-item">
                  <span class="a-color-state">Your Orders</span>
                </span>
              </li>
            </ul>
          </div>
          <div class="row">
            <div class="col-md-6 col-sm-5 col-12">
              <h1 class="a-spacing-medium">Your Orders</h1>
            </div>
          </div>
          <div class="a-row a-spacing-medium custom-view-options">
            <ul class="a-unordered-list a-nostyle a-horizontal">
              <li role="tab">
                <span class="a-list-item"></span>
              </li>
              <li class="selected" role="tab">
                <span class="a-list-item">
                  <span class="item">Orders</span>
                </span>
              </li>
            </ul>
          </div>

          <div class="orderContent">
            <div class="orderContentHeader">
              <div class="row">
                <div class="col-xl-2 col-lg-2 col-md-2 col-sm-2 col-2 text-left">
                  <div class="a-row">
                    <span class="a-size-mini a-color-secondary">ORDER PLACED</span>
                    <br />
                    <span class="a-size-base a-text-bold a-color-secondary">{{showOrderDate}}</span>
                  </div>
                </div>
                <div class="col-xl-2 col-lg-2 col-md-2 col-sm-2 col-2">
                  <div class="a-row">
                    <!-- <span class="a-size-mini a-color-secondary">TOTAL</span>
                    <br />
                    <span class="a-size-base a-text-bold a-color-secondary">Rs.{{totalOrderPrice[index]}}.00</span> -->
                  </div>
                </div>
                <div class="col-xl-4 col-lg-4 col-md-4 col-sm-4 col-3">
                  <div class="a-row">
                    <span class="a-size-mini a-color-secondary">SHIP TO</span>
                    <br />
                    <!-- Owner's name -->
                    <a href class="a-size-base font-weight-bold a-link-normal">
                      {{orderShipName}}
                      <i class="far fa-chevron-down"></i>
                    </a>
                  </div>
                </div>
                <div class="col-xl-4 col-lg-4 col-md-4 col-sm-4 col-5 text-right">
                  <div class="a-row">
                    
                    <!-- <span class="a-size-mini a-color-secondary">ORDER {{eachOrder[index].razorpayOrderId}}</span> -->
                    <br />
                    <a href="#" class="a-size-base font-weight-bold a-link-normal">Order Details</a>
                    &nbsp;
                    <div
                      style="display: inline-block; background-color: #ddd; height: 15px; width: 2px; margin-bottom: -3px;"
                    ></div>&nbsp;
                    <!-- <a href="#" class="a-size-base font-weight-bold a-link-normal">Invoice</a> -->
                  </div>
                </div>
              </div>
            </div>
            <!-- Orders body -->
            <div class="orderContentBodyAlt" v-for="product in products" :key="product._id">
              <div class="a-row">
                <h1
                  class="a-size-medium a-text-bold"
                  style="color: #111 !important;font-family: 'MyWebFont',Arial,sans-serif !important; "
                >
                  <!-- Estimated Delivery -->
                  
                </h1>
              </div>
              <!-- List of products from order -->
              <div>
                <div class="a-spacing-base"></div>
                <div class="row">
                  <div class="col-xl-2 col-lg-2 col-2">
                    <!-- Product's image -->
                    <a href="#">
                      <img class="img-fluid" :src="product.productID.photo" style="width: 100px;" />
                    </a>
                  </div>
                  <div class="col-xl-10 col-lg-10 col-10">
                    <div class="a-row">
                      <span class="a-size-small">
                        <!-- Product title -->
                        <a href="#">{{product.productID.title}}</a>
                      </span>
                    </div>
                    <div class="a-row">
                      <span class="a-size-mini a-color-secondary">Sold by: Brahmapuri-Life-essentials</span>
                    </div>
                    <div class="a-row">
                      <!-- Product quantity -->
                      <span class="a-size-mini" style="color: #111; font-weight: 400;">Quantity: {{product.quantity}}</span>
                    </div>
                    <div class="a-row">
                      <!-- Product price -->
                      <span class="a-size-mini a-color-price">Rs.{{product.price}}</span>
                    </div>
                    <br />
                    <div class="a-row">
                      <!-- <span class="a-button-buy-again">Buy it again</span>
                      <span class="a-button-view-item">View your item</span> -->
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="col-xl-2 col-lg-1 col-md-12"></div>
      </div>
    </div>
    <!--/YOUR ORDER-->
  </main>
  <!--/MAIN-->
  <Footer />
  </div>
</template>

<script>
export default {
  data(){
    return{
      orders:"",
      products:"",
      orderDate: [],
      totalOrderPrice: [],
      orderPlacedDate:[],
      orderShipName: ""
    }
  },
  computed:{
    showOrderDate(){
      let len = this.orders.length
      let ind = len - 1
      return this.orderDate[ind]
    }
  },
  mounted(){
    let v = localStorage.getItem('brahmapuriToken') || this.$cookies.get('brahmapuriToken')

    this.$axios.$get("https://brahmapuri-server.herokuapp.com/api/userorders",{
      headers: {
        "x-access-token": v
      }
    }).then(res=>{
      if(res.success){
        this.orders = res.orders
        console.log("orders", this.orders)
        this.getTotal()
      }
    }).catch(err=>{
      console.log(err)
    })
  },
  methods: {
    getTotal(){
      let getProducts = []
      let getOrderDate = []
      let getOrderShip
      this.orders.map(order=>{
        getProducts.push(order.products)
        getOrderDate.push(order.createdAt)
        getOrderShip = order.owner
      })
      let merged = [].concat.apply([], getProducts);
      getOrderDate.map((dat,index)=>{
        let date = new Date(dat)
        this.orderDate.push(date.toLocaleString('en-GB', {day:'numeric', month: 'long', year:'numeric'}))
      })
        console.log("get order dates", getOrderDate)
      // this.orderDate = getOrderDate
      // this.orderDate = date.toLocaleString('en-GB', {day:'numeric', month: 'long', year:'numeric'})
      this.products = merged
      this.orderShipName = getOrderShip.name
      console.log("filtered orders", getProducts)
      console.log("filtered date", this.orderDate)
      console.log("filtered ship user", this.orderShipName)
      // let total = 0
      // let allTotals = []
      // this.order.map(prod=>{
      //   prod.products.map(eachProd=>{
      //     total += eachProd.price*eachProd.quantity
      //     allTotals.push(total)
      //     total = 0
      //   })
      // })
      // allTotals.map(tot=>{
      //   return tot+Math.ceil(tot * .03)
      // })
      // this.totalOrderPrice = allTotals
      // console.log("alltotals", this.totalOrderPrice)
    }
  }
}
</script>