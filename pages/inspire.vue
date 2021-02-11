<template>
  <v-row >
    <template v-for="item, index in items">
      <v-col cols="12" sm="4" md="4">
      
        <UserListing />
      
      <v-card>
        
      </v-card>
    </v-col>
    </template>
  </v-row>
</template>

<script>
import UserListing from '~/components/UserListing.vue'

export default {
  layout: 'bitssDashboard',
  components: {
    UserListing,
  },
  data () {
    return {
      loading: false,
      selection: 1,
      items: [{},{},{},{},{},{},{},{},{},{},]
    }
  },
  
}
</script>
