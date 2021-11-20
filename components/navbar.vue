<template>
  <v-app-bar fixed app color="white" elevate-on-scroll style="border-bottom: 1px solid #e1e1e1">
    <h3>
      ANO
      <span class="font-weight-regular">NAME</span>
    </h3>
    <v-spacer></v-spacer>
    <v-avatar size="40" v-if="$route.name != 'index'">
      <v-img
        src="https://images.squarespace-cdn.com/content/v1/5bf6023e9772aeb688f70ec0/1549845045984-IVOF0EE52RWX1DN587UO/blackpinkjennie+.jpg?format=500w"
      ></v-img>
    </v-avatar>
  </v-app-bar>
</template>