<template>
  <v-data-table
    v-model="itemSelected"
    class="elavation-1"
    style="width: 800px; margin: 0 auto"
    :hide-default-footer="true"
    :items="data_table_items"
    :single-select="itemSelect"
    show-select
    :headers="data_table_header">

    
    <template v-slot:item.upload_attachment="{ item }">
      <v-tooltip bottom >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            class="d-inline-flex mx-1"
            small
            plain
            fab
            @click="showItemAttachment(item)"
            v-bind="attrs"
            v-on="on">
            <v-icon
              color="grey darken-1"
              small>mdi-file-document-box-search</v-icon>
          </v-btn>
        </template>  
        <span style="font-size: 0.65rem;">{{'View Attachment'|_}}</span>
      </v-tooltip>
    </template>
    
    
    
  </v-data-table>
</template>

<script>


export default {
  layout: 'bitssDashboard',
  components: {},
  data () {
    return {
      data_table_header: [
        { text: ``,align: 'start',value: 'selection_checkbox', width:"30px",sortable:false },
        { text: 'Name' ,align: 'start',value: 'subCategory',sortable:false },
        { text: 'Price' ,align: 'start',value: 'price',sortable:false },
        {text: 'Add to Cart', value: 'buy', width:"120px",sortable: false},
      ],
      data_table_items: [
        { subCategory: 'today.sale', price: '20', type: 'free'},
        { subCategory: 'special.sale', price: '20', type: 'premium'},
        { subCategory: 'anniv.sale', price: '20', type: 'premium'},
        { subCategory: 'todays.promo', price: '20'},
        { subCategory: 'now.promo', price: '20'},
        { subCategory: 'anniv.promo', price: '20'},
        { subCategory: 'reserve.today', price: '20'},
        { subCategory: 'sign-up.today', price: '20'},
        { subCategory: 'promo.today', price: '20'}, 
      ],

    }
  },
  
}
</script>
