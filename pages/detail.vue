<template>
  <CardDetail :api_value="api_value" />
</template>

<script>
import CardDetail from '~/components/CardDetail.vue'

export default {
  layout: 'bitssDashboard',
  components: {
    CardDetail,
  },
  data () {
    return {
      api_value: [
        {product_title: 'Ella Fashion #772-B New Style INS Fashion Desgin Insulation Bag Lunch Bag Cold Bag', img: 'https://cdn.vuetifyjs.com/images/cards/cooking.png', price: '58.00', orig_price: '199.00', discount: '-70%', rating: '4.5', sold_items: '413', sm_width: '2', md_width: '2', cols_width: '12', link: '/detail'  },
        
      ],
    }
  },
  
}
</script>
