<template>  
  <div>
    <h2>Collection</h2>
    <Cards :api_value="api_coupons.data" :item_status="item_status"/>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import Cards from '~/components/Cards.vue'

export default {
  layout: 'bitssDashboard',
  components: {
    Logo,
    Cards
  },
  async asyncData() {
    const api_coupons = await fetch (
      //'https://api.nuxtjs.dev/mountains'
      // 'http://localhost:3005/api/coupon'
      'http://138.68.62.198:8081/v1/core/coupons', 
    {
      method: 'get',
      headers: { 
        'Content-Type': 'application/json',
        "Authorization" : "Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6InRlc3RAdGVzdC5jb20iLCJuYW1lIjoidGVzdCBtZSIsInBlcm1pc3Npb25MZXZlbCI6MX0.vu1blTlYf67J2K6HNwTTMtofv4KjdYp5kdYKUgOapPU"
       },
      
    })
		.then(res => res.json())
		.then(json => {
      console.log(json);
      return(json);
    })
    return { api_coupons }
  },
  data () {
    return {
      item_status: [
        {status: 0},
        {status: 0},
        {status: 1},
      ]
    }
  },

  
}
</script>