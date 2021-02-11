<template>
  
    <v-card
      :loading="loading"
      class="mx-1 my-4"
      max-width="500">
      <template slot="progress">
        <v-progress-linear
          color="deep-purple"
          height="10"
          indeterminate
        ></v-progress-linear>
      </template>

      <v-card-title>Vicc</v-card-title>

      <v-card-text>
        <v-row>
          <v-col
            cols="12"
            sm="6"
            md="6"
          >
            <v-text-field
              label="Fist name"
              required
              dense
              value=" "
              hide-details=true
              outlined
              autofocus
            ></v-text-field>
          </v-col>
          <v-col
            cols="12"
            sm="6"
            md="6"
          >
            <v-text-field
              label="Last name"
              dense
              value=" "
              hide-details=true
              outlined
              required
            ></v-text-field>
          </v-col>
          <v-col
            cols="12"
            sm="6"
            md="6"
          >
            <v-text-field
              label="Phone No."
              required
              dense
              value=" "
              hide-details=true
              outlined
              autofocus
            ></v-text-field>
          </v-col>
          <v-col
            cols="12"
            sm="6"
            md="6"
          >
            <v-text-field
              label="Address"
              dense
              value=" "
              hide-details=true
              outlined
              required
            ></v-text-field>
          </v-col>
        </v-row>
      </v-card-text>

      <v-divider class="mx-4"></v-divider>


      <v-card-actions>
        <v-btn
          color="deep-purple lighten-2"
          text
          @click="reserve"
        >
          Reserve
        </v-btn>
      </v-card-actions>
    </v-card>
  
</template>

<script>