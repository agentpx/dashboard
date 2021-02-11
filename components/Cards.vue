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
  word-break: break-word
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
  -webkit-filter: none;
  filter: none;
}
.link:hover {
  -ms-box-shadow: 0 2px 9px 0 rgba(0, 0, 0, 0.05);
  -o-box-shadow: 0 2px 9px 0 rgba(0, 0, 0, 0.05);
  box-shadow: 0 2px 9px 0 rgba(0, 0, 0, 0.05);
  transform: scale(1.04);
}
.link.disabled {
  pointer-events: none;
  cursor: default;
  opacity: 0.80;
  -ms-box-shadow: 0 2px 9px 0 rgba(0, 0, 0, 0);
  -o-box-shadow: 0 2px 9px 0 rgba(0, 0, 0, 0);
  box-shadow: 0 2px 9px 0 rgba(0, 0, 0, 0);
  -webkit-filter: grayscale(100%) 
          brightness(115%)
          contrast(120%);
  filter: grayscale(100%) 
          brightness(115%)
          contrast(120%);
  
  transition: filter 0.3s, box-shadow 0.3s;
  -webkit-transition: filter 0.3s, -webkit-filter 0.3s, box-shadow 0.3s;
}
</style>
<template>
<v-container fluid>
  <v-row >
    <template v-for="(item, index) in api_value">
      <v-col :cols="cols_width" :sm="sm_width" :xs="xs_width" :md="md_width" :key="item.index">
        <NuxtLink class="link" :class="item.active == 'false' ? 'disabled' : undefined "
         :to="`${item.name}`">
          <v-card class="custom-box-shadow" max-width="200" :key="index">
            <v-img height="160" :src="item.image"></v-img>
            <v-card-title v-text="item.name" class="product_title"></v-card-title>
            <v-card-text>
              <v-row class="mx-0">
                <div class="mt-2 my-2 item_price" v-text="'$'+item.price"></div>
              </v-row>

              <div class="my-2 grey--text" style="font-size: 11px;">
                <v-flex class="text-decoration-line-through d-inline" v-text="item.orig_price"></v-flex> <v-flex class="d-inline" style="color: #000;" v-text="item.discount"></v-flex>
                
              </div>
            
              <v-row no-gutters>
                <v-col cols="6">
                  <v-rating
                    :value="5"
                    color="amber"
                    dense
                    half-increments
                    readonly
                    size="10"
                  ></v-rating>
                </v-col>
                <v-col cols="6" v-if="item.sold_items">
                  <div class="grey--text ml-4"> (<span  v-text="item.sold_items"></span>)
                  </div>
                </v-col>
              </v-row>
            </v-card-text>
        </v-card>
        </NuxtLink>
      </v-col>
    </template>
  </v-row> 
</v-container>
</template>


<script>
export default {
  props: ['api_value', 'item_status'],
  data () {
     return {
        sm_width: '2',
        xs_width: '2',
        md_width: '2',
        cols_width: '6'
     }
  }
}

</script>