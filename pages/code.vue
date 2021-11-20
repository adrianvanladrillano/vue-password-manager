<template>
  <div>
    <v-list-item two-line class="px-0 text-center">
      <v-list-item-content>
        <v-list-item-title class="font-weight-bold title">Set-up Passcode</v-list-item-title>
        <v-list-item-subtitle
          class="text-small text--secondary"
        >Choose what kind of account you want to create.</v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>

    <div align="center" justify="center">
      <v-btn elevation="0" large fab class="ma-3" v-for="i in 10" :key="i">
        <h3>{{i}}</h3>
      </v-btn>
    </div>
  </div>
</template>