<template>
  <v-card style="box-shadow: rgba(0, 0, 0, 0.1) 0px 1px 2px 0px;" @click="$emit('showDialog', 1)">
    <v-list-item two-line class="px-0">
      <v-list-item-avatar tile width="56" height="56">
        <v-img
          style="width: 100%"
          src="https://cdn.vox-cdn.com/thumbor/PHNAzbq1NcE2WnlduuoP_DkY8Hs=/0x0:1000x1000/1400x1050/filters:focal(421x430:581x590):no_upscale()/cdn.vox-cdn.com/uploads/chorus_image/image/62800797/Mastercard_logo.0.jpg"
        ></v-img>
      </v-list-item-avatar>
      <v-list-item-content>
        <v-list-item-title
          class="text-regular font-weight-medium grey--text text--darken-4"
        >BDO Credit Card</v-list-item-title>
        <span class="text-small text--secondary">5335 565 6596</span>

        <v-list-item-subtitle class="text-small">
          <span>Bank</span>
        </v-list-item-subtitle>
      </v-list-item-content>
      <v-list-item-actions>
        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
      </v-list-item-actions>
    </v-list-item>
  </v-card>
</template>
<style>
.text-regular {
  font-size: 0.9em;
}
.text-small {
  font-size: 0.7em;
}
</style>