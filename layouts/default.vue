<template>
  <v-app dark>
    <Navbar v-if="$vuetify.breakpoint.mobile" />
    <Sidebar v-if="!$vuetify.breakpoint.mobile" />
    <v-main style="background: #fff">
      <v-container class="px-7">
        <Nuxt />
      </v-container>
    </v-main>
    <v-fab-transition v-if="$route.name == 'dashboard'">
      <v-btn
        router
        to="/accounts/new"
        style="z-index: 9999;margin-bottom: 100px"
        color="black"
        fab
        dark
        large
        fixed
        absolute
        bottom
        right
      >
        <v-icon>mdi-plus</v-icon>
      </v-btn>
    </v-fab-transition>
    <bottom-nav v-if="$route.name != 'index'" />
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,

      hidden: false,

      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  }
}
</script>
<style>
.text-regular {
  font-size: 0.9em;
}
</style>