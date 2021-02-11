<template>
  
    <CardDetail :api_value="api_item.data" />
    
  
</template>
<script>
import CardDetail from '~/components/CardDetail.vue'

export default {
  layout: 'bitssDashboard',
  components: {
    CardDetail,
  },
  async asyncData({ params, redirect }) {
    const api_item = await fetch (
      //`https://api.nuxtjs.dev/mountains/${params.slug}`
      'http://138.68.62.198:8081/v1/core/coupons', 
      {
        method: 'get',
        headers: { 
          'Content-Type': 'application/json',
          "Authorization" : "Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6InRlc3RAdGVzdC5jb20iLCJuYW1lIjoidGVzdCBtZSIsInBlcm1pc3Npb25MZXZlbCI6MX0.vu1blTlYf67J2K6HNwTTMtofv4KjdYp5kdYKUgOapPU"
        },
      }  
    ).then(res => res.json())
    
    return { api_item }
    const filteredItem = api_item.find(
      (el) =>
        el.name.toLowerCase() === params.name
    )
    if (filteredItem) {
      return {
        name: filteredItem,
      }
    }
    // } else {
    //   redirect('/')
    // }
    
    
  }
}
</script>
