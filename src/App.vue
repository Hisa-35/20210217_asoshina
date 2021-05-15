<template>
  <section class="container">
    <input type="text"  v-model="text"/>
    <button @click="searchAddressInfo">住所自動入力</button>
    <p>Address：{{addressData}}</p>
    <p>create by A.HISA</p>
  </section>
</template>

<script>
const axios = require('axios');


export default {
  data() {
    return {
      zipcode: '',
      addressData: ''
    }
  },
  methods: {
   searchAddressInfo() {
    
    // let url = `https://apis.postcode-jp.com/api/v4/postcodes/${this.text}?apiKey=IPJQQ8yzHDIjySikctA5hy3K2Yy5obbcpC4ra38`;
 let url = `https://apis.postcode-jp.com/api/v4/postcodes/${this.text}?apiKey=IPJQQ8yzHDIjySikctA5hy3K2Yy5obbcpC4ra38`;
  console.log(url)
     axios.get(url).then((res) => {
       console.log("レスポンス",res);
        this.addressData = res.data[0].allAddress
    })
    }
  }
}
</script>