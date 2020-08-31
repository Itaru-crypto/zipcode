<template>
  <div class="home">
      <input type="text" maxlength="7" v-model="zipcode" />
      <button @click="searchAddressInfo">住所自動入力</button>
      <p>Address:{{addressData}}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      zipcode: null,
      addressData: "",
      apiKey: "XRhE2Fd5JwFOSq4oT7GTrzuCy9hFx7FCT0OKTUt",
    }
  },
  methods: {
      searchAddressInfo(){
        let url = 
        "https://apis.postcode-jp.com/api/v3/postcodes/" +
        this.zipcode +
        "?apiKey=" +
        this.apiKey;
      axios.get(url).then((res)=> {
        this.addressData = res.data.allAddress;
      });
    },  
  },
};

</script>
