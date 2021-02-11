<template>  
  <div>
    
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


<!--
 <template>  
   <Cards :api_value="api_value"/>
</template>

<script>
-->
// import Logo from '~/components/Logo.vue'
// import Cards from '~/components/Cards.vue'


// export default {
//   layout: 'bitssDashboard',
//   components: {
//     Logo,
//     Cards
//   },
//   data () {
//     return {
//       loading: false,
//       selection: 1,
//       api_value: [
//         {product_title: 'Extra 20% Off W/ IdealFit Promo Code', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/idealfit_offerlifestyleimage_1.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '01.02.2021', status: 'sold', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: 'BOGO 50% Off OnePlus Buds Z', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/oneplus_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '12.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '30% Off Elfa + Free in-store or Virtual in-home Design Appointment', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/container_store_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '20% Off Valentine\'s Day Coupon | $39 Minimum Spend', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/70c0cae8d75f47c9b860195ae3226a03.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: 'BOGO 50% Off OnePlus Buds Z', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/oneplus_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '12.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '30% Off Elfa + Free in-store or Virtual in-home Design Appointment', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/container_store_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '20% Off Valentine\'s Day Coupon | $39 Minimum Spend', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/70c0cae8d75f47c9b860195ae3226a03.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: 'BOGO 50% Off OnePlus Buds Z', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/oneplus_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '12.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '30% Off Elfa + Free in-store or Virtual in-home Design Appointment', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/container_store_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '20% Off Valentine\'s Day Coupon | $39 Minimum Spend', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/70c0cae8d75f47c9b860195ae3226a03.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: 'BOGO 50% Off OnePlus Buds Z', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/oneplus_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '12.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '30% Off Elfa + Free in-store or Virtual in-home Design Appointment', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/container_store_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '20% Off Valentine\'s Day Coupon | $39 Minimum Spend', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/70c0cae8d75f47c9b860195ae3226a03.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: 'BOGO 50% Off OnePlus Buds Z', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/oneplus_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '12.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '30% Off Elfa + Free in-store or Virtual in-home Design Appointment', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/container_store_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '20% Off Valentine\'s Day Coupon | $39 Minimum Spend', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/70c0cae8d75f47c9b860195ae3226a03.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: 'BOGO 50% Off OnePlus Buds Z', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/oneplus_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '12.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '30% Off Elfa + Free in-store or Virtual in-home Design Appointment', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/container_store_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '20% Off Valentine\'s Day Coupon | $39 Minimum Spend', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/70c0cae8d75f47c9b860195ae3226a03.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: 'BOGO 50% Off OnePlus Buds Z', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/oneplus_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '12.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '30% Off Elfa + Free in-store or Virtual in-home Design Appointment', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/container_store_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '20% Off Valentine\'s Day Coupon | $39 Minimum Spend', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/70c0cae8d75f47c9b860195ae3226a03.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: 'BOGO 50% Off OnePlus Buds Z', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/oneplus_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '12.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '30% Off Elfa + Free in-store or Virtual in-home Design Appointment', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/container_store_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '20% Off Valentine\'s Day Coupon | $39 Minimum Spend', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/70c0cae8d75f47c9b860195ae3226a03.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: 'BOGO 50% Off OnePlus Buds Z', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/oneplus_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '12.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '30% Off Elfa + Free in-store or Virtual in-home Design Appointment', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/container_store_offerlifestyleimage.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
//         {product_title: '20% Off Valentine\'s Day Coupon | $39 Minimum Spend', img: 'https://invitationdigital-res-1.cloudinary.com/image/upload/w_248,h_138,c_fill,q_auto,fl_strip_profile,f_auto/70c0cae8d75f47c9b860195ae3226a03.jpg', price: '58.00', orig_price: '199.00', discount: '-70%', expiry_date: '03.02.2021', rating: '4.5', sold_items: '413', xs_width: '6', sm_width: '2', md_width: '3', cols_width: '6', link: '/detail'  },
        
//       ],
//     }
//   },
  
// }
// </script>
