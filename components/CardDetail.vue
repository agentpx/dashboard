<style>
.v-card.custom-box-shadow:not(.v-sheet--outlined) {
  -ms-box-shadow: 0 2px 9px 0 rgba(0, 0, 0, .08);
  -o-box-shadow: 0 2px 9px 0 rgba(0, 0, 0, .08);
  box-shadow: 0 2px 9px 0 rgba(0, 0, 0, .08)
}
.product_title {
  overflow:hidden; height:53px; 
  -webkit-line-clamp: 2; 
  font-size: 1rem; 
  line-height: 1.3; 
  margin-bottom: 10px; 
  -webkit-box-orient: vertical; 
  display: -webkit-box;
}
.item_price {
  font-size: 18px;
  color: #f57224 !important; 
  font-weight: 600;
}
.link {
  text-decoration: none;
  transition: all .2s ease-in-out; 
  display: block;
}
.link:hover {
  -ms-box-shadow: 0 2px 9px 0 rgba(0, 0, 0, 0.05);
  -o-box-shadow: 0 2px 9px 0 rgba(0, 0, 0, 0.05);
  box-shadow: 0 2px 9px 0 rgba(0, 0, 0, 0.05);
  transform: scale(1.04);
}
</style>

<template>
<v-container fluid>
  <v-row >
    <template v-for="(item, index) in api_value">
      <v-col cols="12" sm="4" md="4" v-if="('/'+item.name) == decodeURI($route.path)" :key="index">
        <v-img :src="item.image"></v-img>
      </v-col>
      <v-col cols="8" sm="8" md="8" v-if="('/'+item.name) == decodeURI($route.path)" :key="item.index">
        <h4 class="transition-swing text-h5 mb-6" v-text="item.name"></h4>
        <p v-text="item.description"></p>
        <v-row no-gutters>
          <v-col cols="6" xs="6">
            <v-rating
              :value="5"
              color="amber"
              class="mb-4"
              dense
              half-increments
              readonly
              size="20"
            ></v-rating>
          </v-col>
          <v-col cols="6" xs="6" v-if="item.sold_items">
            <div class="grey--text"> <span  v-text="item.sold_items"></span> Ratings
            </div>
          </v-col>
        </v-row>
        <div class="mt-2 my-2 item_price text-h4" v-text="'$'+item.price"></div>
        <div class="my-2 grey--text text-h8" >
          <v-flex class="text-decoration-line-through d-inline mr-2" v-text="item.orig_price"></v-flex> <v-flex class="d-inline" style="color: #000;" v-text="item.discount"></v-flex>
        </div>
        <v-divider class="my-3"/>
          <v-btn icon color="pink">
            <v-icon>mdi-heart</v-icon>
          </v-btn>

          <v-btn icon color="indigo">
            <v-icon >mdi-bookmark</v-icon>
          </v-btn>
          <v-menu offset-y>
            <template v-slot:activator="{ on, attrs }">
              <v-btn icon
                color="green"
                v-bind="attrs"
                v-on="on">
                <v-icon>mdi-share-variant</v-icon>
              </v-btn>
            </template>
            <v-list>
              <v-flex
                class="d-inline mx-2" style="max-width:40px;"
                v-for="(item, index) in social"
                :key="index"
              >
                <v-img max-width="18px" :src="item.icon" dark style="background:blue; padding: 20px; border-radius: 30px; background-size: contain;" class="d-inline-block"/>
                
              </v-flex>
            </v-list>
          </v-menu>
        <v-divider class="my-3"/>
        <v-btn
          rounded
          large
          color="primary"
          class="px-10 py-2"
          dark
        >
          REDEEM
        </v-btn>
        <v-btn
          rounded
          large
          color="orange"
          class="px-10 py-2 mx-2"
          dark
        >
          SCAN QR
        </v-btn>

      </v-col>
    </template>
  </v-row> 
</v-container>
</template>


<script>
export default {
  head: {
    title: 'Coufon Detail Page',
    meta: [
      { charset: 'utf-8' },
      { name: 'viewport', content: 'width=device-width, initial-scale=1' },
      {
        hid: 'Coufon.com is a one stop coupon application.',
        name: 'Coufon.com is a one stop coupon application.',
        content: 'Coufon.com is a one stop coupon application.'
      }
    ],
    link: [{ rel: 'icon', type: 'image/x-icon', href: '/favicon.ico' }]
  },
  props: ['api_value'],
  data () {
    return {
      showMenu: false,
      social: [
        {name: 'facebook', icon: 'https://wms-api.logflows.com/october/themes/demo/assets/images/icons/icon-facebook.svg'},
        {name: 'facebook', icon: 'https://wms-api.logflows.com/october/themes/demo/assets/images/icons/icon-facebook.svg'},
      ],
    }
  },
  
}

</script>