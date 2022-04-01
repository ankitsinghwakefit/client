<template>
  <div class="my-footer">
    <b-row class="back-to-top">
      <b-col class="text-center">
        <a href="#" id="navBackToTop"> Back to top </a>
      </b-col>
    </b-row>

    <b-row class="footer-links">
      <b-col sm="6" lg="3" md="6" xl="3"
        ><router-link style="color: white; text-decoration: none" to="/about"
          >About Us</router-link
        ></b-col
      >
      <b-col sm="6" lg="3" md="6" xl="3"
        ><a
          href="https://www.youtube.com/channel/UCQakirfw9oa-wholq9jidfw"
          target="_blank"
          style="color: white; text-decoration: none"
          >Live
          <b-icon-youtube variant="danger" class="mytube"></b-icon-youtube></a
      ></b-col>
      <b-col sm="6" lg="3" md="6" xl="3"
        ><router-link style="color: white; text-decoration: none" to="/location"
          >Our Location</router-link
        ></b-col
      >
      <b-col sm="6" lg="3" md="6" xl="3"
        ><router-link
          style="color: white; text-decoration: none"
          to="/contact"
          class="nav-a"
          >Contact Us</router-link
        ></b-col
      >
    </b-row>

    <b-row class="footer-last-links">
      <span
        ><router-link to="/termsandconditions" class="nav_a"
          >Terms & Conditions</router-link
        ></span
      >
      <span
        ><router-link to="/privacypolicy" class="nav_a"
          >Privacy policy</router-link
        ></span
      >
      <span
        ><router-link to="/returnandrefundpolicy" class="nav_a"
          >Return & Refund Policy</router-link
        ></span
      >
      <span
        ><router-link to="/shippingpolicy" class="nav_a"
          >Shipping Policy</router-link
        ></span
      >
      <span style="color: white; text-decoration: none"
        >© 2003-2022, brahmapuri-life-essentials, Inc. or its affiliates</span
      >
    </b-row>
  </div>
</template>

<style scoped>
.my-footer {
  width: 100%;
}
.back-to-top {
  background-color: #4c8d2b;
  font-size: 18px;
  color: white;
  padding: 20px;
}
.back-to-top a {
  color: white;
  text-decoration: none;
}
.row {
  margin: 0;
}
.footer-links {
  background-color: #0b5a4f;
  padding: 40px;
  font-weight: bold;
}
.footer-last-links {
  background-color: #04362f;
  padding: 20px;
  display: flex;
  justify-content: space-evenly;
}
.nav_a {
  color: white;
  text-decoration: none;
}
</style>

