<template>
  <section class="container">
    <input type="text"  v-model="text"/>
    <button @click="searchAddressInfo">住所自動入力</button>
      <p>Address：{{addressData}}</p>
  </section>
</template>

<script>
const axios = require('axios');

let url = `https://apis.postcode-jp.com/api/v4/postcodes/postcode==${this.text}?apiKey=IPJQQ8yzHDIjySikctA5hy3K2Yy5obbcpC4ra38`;

export default {
  data() {
    return {
      zipcode: '',
      addressData: ''
    }
  },
  methods: {
    searchAddressInfo(
      https://apis.postcode-jp.com/api/v4/postcodes/postcode==${this.text}?apiKey=IPJQQ8yzHDIjySikctA5hy3K2Yy5obbcpC4ra38
    ) {
      axios.get(url).then((res) => {
        // リクエスト送信後以下resにレスポンス（受け取ったデータ）が含まれるので
        // console.logで値の確認を行います dataプロパティの中に住所は含まれております
        console.log(res);
        // オブジェクトのデータの取り出し方については以下教材のオブジェクトへのアクセスを参照してください
        // https://coachtech-lms.com/javascript/javascript-object/2718/
        this.addressData = res.data.results[0];
      })
    }
  }
}
</script>