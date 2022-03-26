<template>
  <div>
    <Navbarnew />
    <main>
      <b-container class="bv-example-row">
        <b-row style="margin: 20px;">
          <iframe
            src="https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d3803.1581759434716!2d74.15312481487926!3d17.595222187954374!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3bc232713cd241f5%3A0x4f1e5923d4962e65!2sSahaja%20Yoga%20Ashram%20Bramhapuri%20(Adishakti%20Mandir)%20H.H.Shree%20Mataji%20Nirmaladevi%20Bramhapuri%2C%20Satara!5e0!3m2!1sen!2sin!4v1641395779777!5m2!1sen!2sin"
            width="1200"
            height="600"
            style="border: 0"
            allowfullscreen=""
            loading="lazy"
          ></iframe>
        </b-row>
      </b-container>
    </main>
    <Footer />
  </div>
</template>

<script>
export default {
   head() {
    return {
      title: "Our Location"
    };
  },
}
</script>