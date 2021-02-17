<template>
  <section class="container">
    <input type="text"  v-model="text"/>
    <button @click="searchAddressInfo">住所自動入力</button>
      <p>Address：{{addressData['address']}}</p>
  </section>
</template>

<script>
const axios = require('axios');

let url = 'postcodejp.address.AutoComplementService(IPJQQ8yzHDIjySikctA5hy3K2Yy5obbcpC4ra38)';

export default {
  data() {
    return {
      zipcode: '',
      addressData: {}
    }
  },
  methods: {
    searchAddressInfo() {
      axios.get(url + this.text).then((res) => {
        this.addressData = res.data.results[0];
      })
    }
  }
}
</script>