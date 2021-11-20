<template>
  <v-app-bar elevation="0" flat>
    <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
    <v-spacer></v-spacer>
    <v-btn icon>
      <v-icon>mdi-magnify</v-icon>
    </v-btn>
  </v-app-bar>
</template>

<script>
export default {
  data() {
    return {
      routes: [{ icon: '', name: '', route: '' }]
    }
  }
}
</script>