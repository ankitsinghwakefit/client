<template>
  <div>
    <Navbarnew />
    <main>
      <b-container class="bv-example-row">
        <b-row style="margin: 20px">
          <div>
            <b-card-group deck>
              <b-card bg-variant="primary" text-variant="white" header="Address" class="text-center">
                <b-card-text><p class="h1 mb-2"><b-icon-map></b-icon-map></p>BRAHMAPURI LIFE ESSENTIALS SPIRITUAL AND RESEARCH FOUNDATION
Sahajyog Asrum Brahmapuri, Rahimatpur Tal-Koregan, Satara, Maharashtra, India, 415511</b-card-text>
              </b-card>

              <b-card bg-variant="secondary" text-variant="white" header="Email us" class="text-center">
                <b-card-text> <p class="h1 mb-2"><b-icon-file-text></b-icon-file-text></p>info@brahmapuri.in</b-card-text>
              </b-card>

              <b-card bg-variant="success" text-variant="white" header="Phone Number" class="text-center">
                <b-card-text><p class="h1 mb-2"> <b-icon-telephone-inbound></b-icon-telephone-inbound></p> 02162 246 139</b-card-text>
              </b-card>
            </b-card-group>
          </div>
        </b-row>
      </b-container>
      <b-container class="bv-example-row">
        <b-row style="margin: 20px;">
          <iframe
            src="https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d3803.1581759434716!2d74.15312481487926!3d17.595222187954374!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3bc232713cd241f5%3A0x4f1e5923d4962e65!2sSahaja%20Yoga%20Ashram%20Bramhapuri%20(Adishakti%20Mandir)%20H.H.Shree%20Mataji%20Nirmaladevi%20Bramhapuri%2C%20Satara!5e0!3m2!1sen!2sin!4v1641395779777!5m2!1sen!2sin"
            width="1140"
            height="600"
            style="border: 0"
            allowfullscreen=""
            loading="lazy"
          ></iframe>
        </b-row>
      </b-container>
    </main>
    <Footernew />
  </div>
</template>

<script>
export default {
   head() {
    return {
      title: "Contact Us"
    };
  },
}
</script>